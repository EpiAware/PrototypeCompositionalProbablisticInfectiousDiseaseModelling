# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Project Setup
```bash
# Initialise git submodules (required after cloning)
git submodule update --init --recursive

# Set up Julia environment (run in Julia REPL)
using Pkg; Pkg.activate("."); Pkg.instantiate()
```

### Main Development Tasks
```bash
# Render the main research document
quarto render

# Run Julia tests (in Julia REPL)
using TestItemRunner; @testitem_run

# Run tests for EpiAware package
cd EpiAware && julia -e "using Pkg; Pkg.activate('.'); Pkg.test()"

# Generate documentation for EpiAware
cd EpiAware && julia --project=docs/ -e "using Pkg; Pkg.instantiate(); using Documenter; include(\"docs/make.jl\")"
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
This is a **compositional epidemiological modelling** research project with two main components:

1. **Main Research Document** (`index.qmd`): Quarto-based manuscript presenting compositional approaches to infectious disease modelling
2. **EpiAware Package** (`EpiAware/` submodule): Core Julia package providing the modelling framework

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
- **Main project**: Uses local path dependency to EpiAware submodule
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
- `index.qmd`: Main research article
- `_quarto.yml`: Multi-format output (HTML, PDF)
- `execute.freeze: false`: Live computation during rendering
- Julia engine integration for reproducible analysis

### Bibliography Management
- BibTeX files in `resources/` directory
- Academic citation style (PLOS Computational Biology)
- Reference integration in Quarto documents

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