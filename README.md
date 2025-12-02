# A Prototype for Compositional Probabilistic Infectious Disease Modelling

[![Render and Deploy Quarto Paper](https://github.com/EpiAware/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/actions/workflows/render-and-deploy.yml/badge.svg)](https://github.com/EpiAware/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/actions/workflows/render-and-deploy.yml)
[![Citation](https://img.shields.io/badge/Cite-CFF-blue)](https://github.com/EpiAware/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/blob/main/CITATION.cff)

## Abstract

Recent outbreaks of Ebola, COVID-19 and mpox have demonstrated the value of modelling for synthesising data for rapid evidence to inform decision making. Effective models require integration of expert domain knowledge from clinical medicine, environmental science, behavioural research, and public health to accurately capture transmission processes, yet current modelling approaches create barriers to this integration. Methods used to synthesise available data broadly fall into pipeline approaches that chain separate models together, or joint models that are often monolithic and difficult to adapt. These barriers have prevented advances across multiple settings where models could have provided actionable insights. Composable models where components can be reused across different contexts and combined in various configurations whilst maintaining statistical rigour could address these limitations. In this work, we start by outlining the key requirements for a composable infectious disease modelling framework and then present a prototype that addresses these requirements through composable epidemiological components built on Julia's type system and Turing.jl. Our approach enables "LEGO-like" model construction where complex models emerge from composing simpler, reusable components. Through three case studies using the prototype, we show how components can be reused across different models whilst maintaining statistical rigour. The first replicates a COVID-19 analysis for South Korea using renewal processes with time-varying reproduction numbers. The second extends these components with reporting delays and day-of-week effects for real-time nowcasting applications. The third integrates ODE solvers for compartmental disease transmission models applied to influenza outbreak data. We explore other potential options and compare them to our proposed approach. The prototype demonstrates promise but future work is needed to solve remaining composability challenges, expand the component library, and integrate bridges to existing epidemiological software ecosystems.

📖 **[Read the paper](https://epiaware.org/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/paper.pdf)** (PDF)

🌐 **[Read the paper online](https://epiaware.org/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/paper.html)** (HTML)

📑 **[Supplementary Information: Case Studies](https://epiaware.org/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/case-studies.html)** (HTML)

📚 **[EpiAware.jl Documentation](https://cdcgov.github.io/Rt-without-renewal/dev/)**

📦 **[EpiAwareR: R Interface](https://github.com/sbfnk/EpiAwareR)**

## Citation

*Citation information will be added upon publication.*

## Prerequisites

### 1. Quarto

Follow the instructions at [quarto.org](https://quarto.org/docs/get-started/) to install Quarto.

### 2. Julia

Follow the instructions at [juliaup](https://github.com/JuliaLang/juliaup) to install Julia using the official Julia version manager.

### 3. Task (Optional)

Install [Task](https://taskfile.dev/installation/) for automated workflow management.

## Executing the Analysis

### Using Task (Recommended)

```bash
task
```

This automatically handles git submodules, Julia environment setup, Quarto extension installation, and document rendering.

Available tasks:
- `task` - Render all documents (default)
- `task render-case-studies` - Render case studies (generates figures)
- `task render-index` - Render main document
- `task preview` - Preview document with live reload
- `task repl` - Launch Julia REPL with project environment
- `task install-extensions` - Install Quarto extensions
- `task --list` - Show all available tasks

### Manual Execution

1. Install Julia 1.11.6 (we expect any version of 1.11 to work well):
   ```bash
   juliaup add 1.11.6
   juliaup override set 1.11.6
   ```

2. Initialise git submodules:
   ```bash
   git submodule update --init --recursive
   ```

3. Set up Julia environment:
   ```bash
   julia +1.11.6
   ```

   Then in the Julia REPL:
   ```julia
   using Pkg
   Pkg.activate(".")
   Pkg.instantiate()
   ```

4. Render the document:
   ```bash
   quarto render
   ```

## Running Interactively

### Case Studies (Julia)

The case studies in `case-studies.qmd` can be run interactively using Quarto's preview mode:

1. Set up the environment:
   ```bash
   task instantiate
   ```

2. Preview with live reload:
   ```bash
   task preview
   ```

   Or open `case-studies.qmd` directly in VS Code or another editor with Quarto support.

### EpiAwareR Vignettes (R)

The `EpiAwareR/` submodule contains R vignettes demonstrating the R interface to EpiAware:

- `EpiAwareR.Rmd` - Getting started guide
- `mishra-case-study.Rmd` - Replicating Mishra et al. (2020) COVID-19 analysis
- `epinow2-comparison.Rmd` - Comparison with EpiNow2 workflows

To run the vignettes interactively:

1. Set up EpiAwareR with Julia backend:
   ```bash
   task setup-epiawarer
   ```

2. Open the vignettes in RStudio or VS Code:
   ```
   EpiAwareR/vignettes/EpiAwareR.Rmd
   EpiAwareR/vignettes/mishra-case-study.Rmd
   EpiAwareR/vignettes/epinow2-comparison.Rmd
   ```

3. Run code chunks interactively using your IDE's execution features.
