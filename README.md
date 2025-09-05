# PrototypeCompositionalProbablisticInfectiousDiseaseModelling
An outline of a prototype approach for compositional infectious disease modelling

## Prerequisites

The analysis for this paper was generated using Julia 1.11.6. We supply `Project.toml` and `Manifest.toml` files for a static environment but you may need to install Julia first.

### Julia Installation

We recommend using [juliaup](https://github.com/JuliaLang/juliaup), the official Julia version manager, for easy installation and management of Julia versions.

#### Quick Setup (Recommended)

If you have [Task](https://taskfile.dev/) installed, you can set up Julia with a single command:

```bash
task julia:setup
```

This will automatically:
- Install juliaup (if not already installed)
- Install Julia 1.11.6
- Configure your environment

#### Manual Installation

##### 1. Install juliaup

**macOS/Linux/FreeBSD:**
```bash
curl -fsSL https://install.julialang.org | sh
```

**macOS (Homebrew):**
```bash
brew install juliaup
```

**Windows:**
- Install from the [Microsoft Store](https://www.microsoft.com/store/apps/9NJNWW8PVKMN)
- Or use winget: `winget install --id 9NJNWW8PVKMN -e`

##### 2. Install Julia 1.11.6

After installing juliaup:
```bash
juliaup add 1.11.6
juliaup default 1.11.6
```

##### 3. Verify Installation

```bash
julia --version
```

#### Alternative Methods

You can also use our automated tasks for specific steps:

```bash
# Check if juliaup is installed
task julia:check-juliaup

# Install juliaup only
task julia:install-juliaup

# Install Julia 1.11.6 only (requires juliaup)
task julia:install-julia

# Install a different Julia version
task julia:install-julia-version VERSION=1.10.0

# Show all Julia setup options
task julia:help
```

#### Troubleshooting

If you encounter issues:

1. **Path not found**: Restart your shell or run `source ~/.bashrc` (or equivalent) after installation
2. **Permission errors**: Make sure you have appropriate permissions or use the package manager for your OS
3. **Multiple Julia installations**: Use `juliaup status` to see all installed versions and `juliaup default <version>` to set the default

For more detailed information, visit the [juliaup documentation](https://github.com/JuliaLang/juliaup).
