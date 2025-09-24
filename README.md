# A Prototype for Compositional Probabilistic Infectious Disease Modelling

## Abstract

Recent outbreaks of Ebola, COVID-19 and mpox have demonstrated the value of modelling for synthesising data for rapid evidence to inform decision making. Effective models require integration of expert domain knowledge from clinical medicine, environmental science, behavioural research, and public health to accurately capture transmission processes, yet current modelling approaches create barriers to this integration. Methods used to synthesise available data broadly fall into pipeline approaches that chain separate models together, or joint models that are often monolithic and difficult to adapt. These barriers have prevented advances across multiple settings where models could have provided actionable insights. Composable models where components can be reused across different contexts and combined in various configurations whilst maintaining statistical rigour could address these limitations. In this work, we start by outlining the key requirements for a composable infectious disease modelling framework and then present a prototype that addresses these requirements through composable epidemiological components built on Julia's type system and Turing.jl. Our approach enables "LEGO-like" model construction where complex models emerge from composing simpler, reusable components. Through three case studies using the prototype, we show how components can be reused across different models whilst maintaining statistical rigour. The first replicates a COVID-19 analysis for South Korea using renewal processes with time-varying reproduction numbers. The second extends these components with reporting delays and day-of-week effects for real-time nowcasting applications. The third integrates ODE solvers for compartmental disease transmission models applied to influenza outbreak data. Across all case studies, the same core components combine differently to address distinct epidemiological questions. We explore other potential options and compare them to our proposed approach. The prototype demonstrates promise but future work is needed to solve remaining composability challenges, expand the component library, and integrate bridges to existing epidemiological software ecosystems.

📖 **[Read the paper](https://epiaware.org/PrototypeCompositionalProbablisticInfectiousDiseaseModelling/index.pdf)**

📚 **[EpiAware.jl Documentation](https://cdcgov.github.io/Rt-without-renewal/dev/)**

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

This automatically handles git submodules, Julia environment setup, and Quarto rendering.

Available tasks:
- `task` - Complete workflow (default)
- `task preview` - Preview document with live reload
- `task repl` - Launch Julia REPL with project environment
- `task --list` - Show all available tasks

### Manual Execution

1. Install Julia 1.11.6 (we expect any version of 1.11 to work well):
   ```bash
   juliaup install 1.11.6
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
