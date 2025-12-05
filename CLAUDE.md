# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Project Setup
```bash
# Initialise git submodules (required after cloning)
git submodule update --init --recursive

# Set up Julia environment (run in Julia REPL)
using Pkg; Pkg.activate("."); Pkg.instantiate()

# Restore R environment for EpiAwareR (in terminal)
Rscript -e 'renv::restore()'
```

### Main Development Tasks
```bash
# Render the main research document
quarto render

# Preview document with live reload
quarto preview

# Run Julia tests (in Julia REPL)
using TestItemRunner; @testitem_run

# Run tests for EpiAware package
cd EpiAware/EpiAware && julia -e "using Pkg; Pkg.activate('.'); Pkg.test()"

# Generate documentation for EpiAware
cd EpiAware/EpiAware && julia --project=docs/ -e "using Pkg; Pkg.instantiate(); using Documenter; include(\"docs/make.jl\")"
```

### Using Task (Recommended)
```bash
# Render all documents (case studies first, then main paper)
task

# Render case studies only (generates figures)
task render-case-studies

# Render main document only
task render-index

# Preview document with live reload
task preview

# Launch Julia REPL with project environment
task repl

# Install Quarto extensions
task install-extensions

# Restore R environment from renv.lock
task renv-restore

# Set up EpiAwareR with Julia backend
task setup-epiawarer

# List all available tasks
task --list
```

### Code Quality
```bash
# Format Julia code (in Julia REPL)
using JuliaFormatter; format(".")

# Run pre-commit hooks
pre-commit run --all-files
```

## Architecture Overview

### Project Structure
This is a **compositional epidemiological modelling** research project with the following components:

1. **Main Research Document** (`index.qmd`): Quarto-based manuscript presenting compositional approaches to infectious disease modelling
2. **Supplementary Information** (`case-studies.qmd`): Full implementation details for case studies, generates figures used in main text
3. **EpiAware Package** (`EpiAware/` submodule): Core Julia package providing the modelling framework
4. **EpiAwareR** (`EpiAwareR/` submodule): R interface to EpiAware using JuliaCall

### Key Technical Stack
- **Julia 1.11+**: Primary language for scientific computing
- **Quarto**: Reproducible research documents and manuscripts
- **Turing.jl**: Probabilistic programming framework
- **TestItemRunner.jl**: Modern Julia testing framework

### EpiAware Package Architecture
The EpiAware package uses a highly **modular, composable design**:

```
EpiAware/src/
├── EpiAwareBase/      # Core abstractions and interfaces
├── EpiAwareUtils/     # Utility functions
├── EpiLatentModels/   # Latent process models (e.g., random walks)
├── EpiInfModels/      # Infection process models
├── EpiObsModels/      # Observation models
└── EpiInference/      # Bayesian inference methods
```

**Key Design Principle**: "Swap-in/swap-out" model components allow users to compose different epidemiological models from reusable parts rather than building monolithic implementations.

### Dependencies Management
- **Julia (main project)**: Uses local path dependency to EpiAware submodule via `Project.toml`/`Manifest.toml`
- **R (EpiAwareR)**: Managed via `renv` with lockfile at `renv.lock`
- **EpiAware package**: Strict version compatibility constraints in `Project.toml`
- **Core dependencies**: Turing.jl, DynamicPPL, Distributions.jl, OrdinaryDiffEq.jl

### Git Workflow
- **Submodule structure**: EpiAware is developed as separate repository
- **Main branch**: Primary development branch
- **CODEOWNERS**: Defined in EpiAware submodule

## Julia Development Patterns

### Code Organisation
- Use `@doc raw" "` for docstrings with LaTeX math
- Internal functions prefixed with `.`
- Modular structure with clear separation of concerns
- Type stability crucial for performance

### Testing Conventions
- `TestItemRunner.jl` for modern test organisation
- Tests mirror source structure in `test/` directory
- Use `@testitem` blocks for test isolation
- `Aqua.jl` for package quality checks

### Documentation Standards
- Comprehensive docstrings for all public functions
- Mathematical notation using LaTeX in docstrings
- Examples in docstrings where appropriate
- Auto-generated documentation via Documenter.jl

## Quarto Integration

### Manuscript Development
- `index.qmd`: Main research article (references figures from `figures/`)
- `case-studies.qmd`: Supplementary Information with full case study code (generates figures)
- `_quarto.yml`: Multi-format output (HTML, PDF), renders case-studies.qmd first then index.qmd
- `execute.freeze: auto`: Cached computation during rendering
- Julia engine integration for reproducible analysis
- Figures saved to `figures/` directory by case-studies.qmd for use in index.qmd

### Bibliography Management
- BibTeX files in `resources/` directory
- Academic citation style (PLOS Computational Biology)
- Reference integration in Quarto documents

### Submission Materials
- `cover-letter.md`: Cover letter for PLOS Computational Biology submission, explaining scope fit for Epidemiology & Public Health section

## Resources Directory

The `resources/` directory contains research materials, literature, and supporting documentation. See `resources/CLAUDE.md` for detailed guidance on the contents and organisation.

## CI/CD Pipeline

The EpiAware submodule includes comprehensive automation:
- **Testing**: Multi-version Julia testing
- **Documentation**: Auto-deployment to GitHub Pages
- **Benchmarking**: Performance regression detection
- **Code coverage**: Codecov integration
- **Dependency updates**: CompatHelper automation
- **Pre-commit hooks**: Code quality enforcement

## Research Context

This project addresses **compositional approaches to infectious disease modelling**, enabling researchers to:
- Build complex epidemiological models from reusable components
- Compare different modelling assumptions systematically
- Reduce implementation barriers for methodological advances
- Ensure reproducible and transparent model development

The work bridges mathematical epidemiology, probabilistic programming, and software engineering to create more flexible and accessible tools for public health decision-making.