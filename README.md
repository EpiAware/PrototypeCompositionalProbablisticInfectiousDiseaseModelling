# PrototypeCompositionalProbablisticInfectiousDiseaseModelling

An outline of a prototype approach for compositional infectious disease modelling

## Executing the Analysis

Run

```bash
quarto render
```

## Prerequisites

### 1. Git Submodules

This repository uses git submodules. After cloning, initialise the submodules:

```bash
git submodule update --init --recursive
```

### 2. Quarto

Follow the instructions at [quarto.org](https://quarto.org/docs/get-started/) to install Quarto.

### 3. Julia 1.11.6

The analysis was generated using Julia 1.11.6. We supply `Project.toml` and `Manifest.toml` files for a static environment.

#### Julia Installation with `juliaup`

We recommend using [juliaup](https://github.com/JuliaLang/juliaup), the official Julia version manager:

1. Install juliaup:
   ```bash
   curl -fsSL https://install.julialang.org | sh
   ```

2. Install Julia 1.11.6 (we expect any version of 1.11 to work well):
   ```bash
   juliaup install 1.11.6
   juliaup 1.11.6
   ```

#### Setting up the Julia Environment

After installing Julia and initialising submodules:

1. Start Julia in the project directory
2. Activate and instantiate the project environment:
   ```julia
   using Pkg
   Pkg.activate(".")
   Pkg.instantiate()
   ```
