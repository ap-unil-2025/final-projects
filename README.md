# AP2025 Final Project Templates

Professional-grade project templates for Advanced Programming MSc course, covering diverse domains in computational finance, actuarial science, operations research, and data science.

---

## 📚 Available Templates

| Template                               | Domain              | Description                                               | Difficulty |
| -------------------------------------- | ------------------- | --------------------------------------------------------- | ---------- |
| [**econgames**](https://github.com/ap-unil-2025/econgames-template)   | Game Theory         | Monte Carlo simulator for repeated normal-form games      | ⭐⭐⭐     |
| [**simclt**](https://github.com/ap-unil-2025/simclt-template)         | Actuarial Science   | Stochastic chain-ladder reserving with bootstrap          | ⭐⭐⭐⭐   |
| [**riskcalc**](https://github.com/ap-unil-2025/riskcalc-template)     | Risk Management     | VaR, CVaR, and portfolio optimization toolkit             | ⭐⭐⭐     |
| [**timeseries**](https://github.com/ap-unil-2025/timeseries-template) | Econometrics        | Time series analysis and forecasting (ARIMA, etc.)        | ⭐⭐⭐⭐   |
| [**mlfinance**](https://github.com/ap-unil-2025/mlfinance-template)   | ML/Finance          | Machine learning for financial prediction and backtesting | ⭐⭐⭐⭐⭐ |
| [**qsim**](https://github.com/ap-unil-2025/qsim-template)             | Operations Research | Discrete-event queue simulator for performance analysis   | ⭐⭐⭐⭐   |
| [**pymort**](https://github.com/ap-unil-2025/pymort-template)         | Actuarial Finance   | Longevity bond pricing and mortality modeling             | ⭐⭐⭐⭐⭐ |

---

## 🚀 Quick Start (For Students)

1. **Choose a template** based on your interests
2. **Use as GitHub template** - Click "Use this template" button
3. **Clone your repository**
   ```bash
   git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
   cd YOUR-REPO
   ```
4. **Set up environment**
   ```bash
   pip install uv
   make install-dev
   ```
5. **Start coding!**
   ```bash
   make check  # Run all quality checks
   make test   # Run tests with coverage
   ```

---

## 🏗️ Template Structure

Every template follows this unified structure:

```
{template}-template/
├── src/{package}/           # Source code
│   ├── __init__.py         # Package with version
│   ├── cli.py              # Command-line interface
│   └── py.typed            # Type checking marker
├── tests/                   # Test suite (≥80% coverage)
│   └── test_*.py
├── pyproject.toml          # Project configuration
├── Makefile                # Development commands
├── README.md              # Quick start guide
├── PROJECT_SPECIFICATION.md # Detailed requirements
├── CONTRIBUTING.md        # Development guidelines
├── LICENSE                # MIT License
└── .github/workflows/     # CI/CD pipelines
```

---

## 🛠️ Development Workflow

All templates support these commands:

```bash
make install-dev    # Set up development environment
make check          # Run ALL quality checks
make test           # Run tests with coverage
make fix            # Auto-fix code issues
make ci             # Simulate full CI pipeline
```

---

## 🎓 Learning Objectives

Students will master:

- **Software Engineering**: Professional Python development practices
- **Domain Expertise**: Deep knowledge in chosen field
- **Type Safety**: Strict type checking with MyPy
- **Testing**: Comprehensive test suites with Hypothesis
- **DevOps**: CI/CD pipelines and automation
- **Documentation**: Clear, professional documentation
- **Version Control**: Git best practices

---

## 📊 Quality Standards

All projects must meet:

| Standard          | Requirement                          |
| ----------------- | ------------------------------------ |
| **Type Checking** | MyPy strict mode, zero errors        |
| **Code Quality**  | Ruff linting, consistent formatting  |
| **Testing**       | ≥80% coverage, property-based tests  |
| **Security**      | Bandit scan, no high-severity issues |
| **Documentation** | Google-style docstrings              |
| **CI/CD**         | All checks pass on GitHub Actions    |

---

## 📚 Template Details

### [EconGames](https://github.com/ap-unil-2025/econgames-template) - Game Theory Simulation

Simulate repeated games like Prisoner's Dilemma, implement strategies (Tit-for-Tat, Grim Trigger), and analyze evolutionary dynamics.

**Key Topics**: Game theory, Monte Carlo simulation, strategy optimization

### [SimCLT](https://github.com/ap-unil-2025/simclt-template) - Chain-Ladder Reserving

Implement Mack chain-ladder method for insurance reserving with bootstrap-based predictive distributions.

**Key Topics**: Actuarial science, bootstrap methods, claims reserving

### [RiskCalc](https://github.com/ap-unil-2025/riskcalc-template) - Risk Measurement

Calculate VaR, CVaR, and optimize portfolios using mean-variance, minimum variance, and risk parity approaches.

**Key Topics**: Risk management, portfolio theory, optimization

### [TimeSeries](https://github.com/ap-unil-2025/timeseries-template) - Time Series Analysis

Fit ARIMA models, detect structural breaks, generate forecasts with prediction intervals.

**Key Topics**: Econometrics, time series, forecasting

### [MLFinance](https://github.com/ap-unil-2025/mlfinance-template) - ML for Finance

Build ML models for financial prediction with rigorous backtesting and feature engineering.

**Key Topics**: Machine learning, finance, backtesting

### [QSIM](https://github.com/ap-unil-2025/qsim-template) - Queueing Simulation

Simulate queueing systems (M/M/1, M/M/c, networks) for performance analysis and optimization.

**Key Topics**: Operations research, discrete-event simulation, queueing theory

### [PyMort](https://github.com/ap-unil-2025/pymort-template) - Longevity Bond Pricing

Model mortality dynamics (Lee-Carter, CBD), price longevity bonds, and analyze longevity risk.

**Key Topics**: Actuarial finance, stochastic modeling, derivatives pricing

---

## 🔧 Technology Stack

All templates use:

- **Python 3.10+** - Modern Python features
- **NumPy/Pandas** - Numerical computing
- **SciPy** - Scientific computing
- **Typer** - CLI interfaces
- **pytest** - Testing framework
- **Hypothesis** - Property-based testing
- **Ruff** - Linting and formatting
- **MyPy** - Static type checking
- **uv** - Fast package manager

Plus domain-specific libraries (statsmodels, scikit-learn, SimPy, etc.)

---

## 📄 License

All templates are released under the **MIT License**.

---

## 🤝 Contributing

Found an issue or want to improve a template?

1. Fork the template repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📞 Support

- **Office Hours**: Check course calendar
- **Discussion Forum**: Course Discord/Slack/Moodle
- **GitHub Issues**: Report bugs in individual template repos

---

## 🎉 Acknowledgments

These templates were developed for the **Advanced Programming 2025** MSc course at UNIL, combining:

- Modern software engineering practices
- Rigorous domain-specific requirements
- Professional development workflows
- Real-world applicability
