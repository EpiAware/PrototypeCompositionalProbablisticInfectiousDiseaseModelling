# PrototypeCompositionalProbablisticInfectiousDiseaseModelling

An outline of a prototype approach for compositional infectious disease modelling

## Prerequisites

### 1. Quarto

Follow the instructions at [quarto.org](https://quarto.org/docs/get-started/) to install Quarto.

### 2. Julia 1.11.6 with juliaup

We recommend using [juliaup](https://github.com/JuliaLang/juliaup), the official Julia version manager:

1. Install juliaup:
   ```bash
   curl -fsSL https://install.julialang.org | sh
   ```

2. Install Julia 1.11.6 (we expect any version of 1.11 to work well):
   ```bash
   juliaup install 1.11.6
   ```

### 3. Task (Optional)

Install [Task](https://taskfile.dev/installation/) for automated workflow management.

## Executing the Analysis

### Using Task (Recommended)

```bash
task
```

This automatically handles git submodules, Julia environment setup, and Quarto rendering.

Available tasks:
- `task` - Complete workflow (default)
- `task preview` - Preview document with live reload
- `task repl` - Launch Julia REPL with project environment
- `task --list` - Show all available tasks

### Manual Execution

1. Initialise git submodules:
   ```bash
   git submodule update --init --recursive
   ```

2. Set up Julia environment:
   ```julia
   using Pkg
   Pkg.activate(".")
   Pkg.instantiate()
   ```

3. Render the document:
   ```bash
   quarto render
   ```

4. For interactive Julia REPL with project environment:
   ```bash
   julia
   ```
   Then in Julia:
   ```julia
   using Pkg; Pkg.activate(".")
   ```
