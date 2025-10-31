# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **meta-repository** for AP2025 (Advanced Programming 2025) final project templates at UNIL. It contains documentation and setup instructions for creating 7 different project templates, but does NOT contain the actual template implementations themselves.

The templates are meant to be created as separate GitHub repositories that students will use as starting points for their MSc projects.

## Available Templates

Seven professional-grade project templates across different domains:

1. **econgames-template** - Game Theory: Monte Carlo simulator for repeated normal-form games
2. **simclt-template** - Actuarial Science: Stochastic chain-ladder reserving with bootstrap
3. **riskcalc-template** - Risk Management: VaR, CVaR, and portfolio optimization toolkit
4. **riskcalc-template** - Risk Management: VaR, CVaR, and portfolio optimization
5. **timeseries-template** - Econometrics: Time series analysis and forecasting (ARIMA)
6. **mlfinance-template** - ML/Finance: Machine learning for financial prediction
7. **qsim-template** - Operations Research: Discrete-event queue simulator
8. **pymort-template** - Actuarial Finance: Longevity bond pricing and mortality modeling

## Technology Stack

All templates are designed to use:
- **Python 3.10+** as the base language
- **uv** for package and virtual environment management
- **NumPy/Pandas/SciPy** for numerical computing
- **Typer** for CLI interfaces
- **pytest** with **Hypothesis** for testing (80%+ coverage required)
- **Ruff** for linting and formatting
- **MyPy** in strict mode for type checking
- **Bandit** for security scanning
- **Makefile** for standardized development commands

## Expected Template Structure

Each template follows this unified structure:
```
{template}-template/
├── src/{package}/           # Source code with __init__.py, cli.py, py.typed
├── tests/                   # Test suite (≥80% coverage)
├── pyproject.toml          # Project configuration
├── Makefile                # Development commands
├── README.md              # Quick start guide
├── PROJECT_SPECIFICATION.md # Detailed requirements
├── CONTRIBUTING.md        # Development guidelines
├── .github/workflows/ci.yml # CI/CD pipeline
└── LICENSE                # MIT License
```

## Common Development Commands (for templates)

Templates should support these Makefile targets:
```bash
make install-dev    # Set up development environment using uv
make check          # Run ALL quality checks (lint, type, test, security)
make test           # Run tests with coverage
make fix            # Auto-fix code issues with ruff
make ci             # Simulate full CI pipeline
make type-check     # Run MyPy type checking
make lint           # Run Ruff linting
make format         # Format code with Ruff
make security       # Run Bandit security scan
```

## Quality Standards

All templates must enforce:
- **Type Checking**: MyPy strict mode with zero errors
- **Code Quality**: Ruff linting with no errors, 100-character line limit
- **Testing**: ≥80% coverage with property-based tests (Hypothesis)
- **Security**: Bandit scan passing, no high-severity issues
- **Documentation**: Google-style docstrings for all public APIs

## Key Documentation Files

- **README.md** - Main repository overview with template descriptions
- **INSTRUCTOR_SETUP.md** - Comprehensive guide for instructors on creating and managing templates
- **.gitignore** - Standard Python gitignore

## Important Context

- This is an **instructor-facing repository** for course setup, not a student-facing codebase
- The actual template code should be created in separate repositories
- Each template repository should be marked as a GitHub template repository
- Students will use GitHub's "Use this template" feature to start their projects
- Templates are designed for an MSc-level Advanced Programming course
- Focus is on combining professional software engineering practices with domain-specific knowledge

## Working with This Repository

When modifying documentation:
- Update README.md for student-facing template descriptions
- Update INSTRUCTOR_SETUP.md for instructor guidance on template management
- Ensure consistency across all documentation
- Keep quality standards and technology stack aligned across all template descriptions
