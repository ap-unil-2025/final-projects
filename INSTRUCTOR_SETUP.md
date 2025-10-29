# Instructor Setup Guide
## AP2025 Final Project Templates

This guide explains how to set up and manage the final project templates for your Advanced Programming course.

---

## 📚 Template Overview

We have created **7 professional-grade project templates**, each following a unified structure with comprehensive tooling:

| Template | Domain | Key Technologies | Difficulty |
|----------|--------|------------------|------------|
| **econgames-template** | Game Theory | NumPy, Monte Carlo | Medium |
| **simclt-template** | Actuarial Science | NumPy, Pandas, Bootstrap | Medium-Hard |
| **riskcalc-template** | Risk Management | NumPy, SciPy, Optimization | Medium |
| **timeseries-template** | Econometrics | statsmodels, ARIMA | Medium-Hard |
| **mlfinance-template** | ML/Finance | scikit-learn, Backtesting | Hard |
| **qsim-template** | Operations Research | SimPy, Queueing Theory | Medium-Hard |
| **pymort-template** | Actuarial Finance | statsmodels, Stochastic Models | Hard |

---

## 🚀 GitHub Setup

### Step 1: Create Template Repositories

For each template directory, create a new GitHub repository:

```bash
# Navigate to template directory
cd econgames-template

# Create GitHub repository (requires gh CLI)
gh repo create ap-unil-2025/econgames-template --public --source=. --push

# Mark as template repository
gh api repos/ap-unil-2025/econgames-template \
  --method PATCH \
  -f is_template=true
```

Or manually via GitHub web interface:
1. Create new repository: `https://github.com/new`
2. Name it: `{template-name}-template` (e.g., `econgames-template`)
3. Set visibility: **Public**
4. Do NOT initialize with README (already exists)
5. Push existing code:
   ```bash
   git remote add origin https://github.com/ap-unil-2025/econgames-template.git
   git branch -M main
   git push -u origin main
   ```
6. Go to Settings → Check "Template repository"

### Step 2: Repeat for All Templates

```bash
# Automate for all templates
for template in econgames simclt riskcalc timeseries mlfinance qsim pymort; do
  cd ${template}-template
  gh repo create ap-unil-2025/${template}-template --public --source=. --push
  gh api repos/ap-unil-2025/${template}-template --method PATCH -f is_template=true
  cd ..
done
```

### Step 3: Configure Repository Settings

For each template repository:

1. **Branch Protection** (Settings → Branches):
   - Protect `main` branch
   - Require pull request reviews before merging
   - Require status checks to pass (CI)

2. **Enable GitHub Actions** (Actions tab):
   - Click "I understand my workflows, go ahead and enable them"

3. **Add Topics** (About section):
   - `python`, `template`, `advanced-programming`, `msc-project`
   - Add domain-specific tags (e.g., `game-theory`, `actuarial-science`)

4. **Update Repository Description**:
   - Example: "Template for Monte Carlo game theory simulation projects - AP2025"

---

## 📖 Student Instructions

### How Students Use Templates

Create a **STUDENT_GUIDE.md** in each template:

```markdown
# Getting Started with This Template

## 1. Create Your Project

### Option A: Use as Template (Recommended)
1. Click the green "Use this template" button
2. Name your repository (e.g., `econgames-yourname`)
3. Set visibility to **Private** (unless you want it public)
4. Clone your new repository

### Option B: Fork
1. Fork this repository
2. Rename it to `{project}-yourname`
3. Clone your fork

## 2. Set Up Development Environment

```bash
# Clone your repository
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
cd YOUR-REPO

# Install uv (if not already installed)
pip install uv

# Set up development environment
make install-dev

# Verify setup
make check
```

## 3. Development Workflow

```bash
# Run tests
make test

# Check code quality
make check

# Auto-fix issues
make fix

# Run full CI pipeline locally
make ci
```

## 4. Project Requirements

- ✅ Implement all TODOs in the codebase
- ✅ Maintain 80%+ test coverage
- ✅ Pass all type checks (MyPy strict mode)
- ✅ Pass all linting checks (Ruff)
- ✅ Write comprehensive documentation
- ✅ Tag release as `v1.0.0` when complete
- ✅ Publish to TestPyPI

## 5. Submission

1. Ensure all commits are pushed to GitHub
2. Create a release tagged `v1.0.0`
3. Submit repository URL via course platform
4. Include link to TestPyPI package

See `PROJECT_SPECIFICATION.md` for detailed requirements.
```

---

## 🏗️ Template Structure

All templates follow this unified structure:

```
{template}-template/
├── .editorconfig              # Editor configuration
├── .gitignore                 # Python .gitignore
├── .pre-commit-config.yaml    # Pre-commit hooks (ruff, mypy, bandit)
├── .secrets.baseline          # Security scanning baseline
├── .github/
│   └── workflows/
│       └── ci.yml            # GitHub Actions CI (to be added)
├── CONTRIBUTING.md           # Development guidelines
├── LICENSE                   # MIT License
├── Makefile                  # Development commands
├── PROJECT_SPECIFICATION.md  # Detailed project requirements
├── README.md                # Quick start guide
├── pyproject.toml           # Project configuration
│   ├── [build-system]       # setuptools
│   ├── [project]            # metadata, dependencies
│   ├── [tool.ruff]          # Linting & formatting
│   ├── [tool.mypy]          # Type checking (strict mode)
│   ├── [tool.pytest]        # Testing (80% coverage required)
│   └── [tool.coverage]      # Coverage configuration
├── src/
│   └── {package}/
│       ├── __init__.py      # Package exports with __version__
│       ├── py.typed         # PEP 561 type marker
│       └── ...              # Implementation files
└── tests/
    └── test_smoke.py        # Basic import test
```

---

## ⚙️ Development Tools Required

Students will need:

- **Python 3.10+**: All templates require Python ≥3.10
- **uv**: Modern Python package manager (recommended)
  ```bash
  pip install uv
  ```
- **git**: Version control
- **make**: Build automation (pre-installed on Linux/macOS, install on Windows)
- **GitHub Account**: For hosting repositories

Optional but recommended:
- **VSCode** with Python extension
- **pre-commit**: For git hooks (installed via `make install-dev`)

---

## 🧪 Quality Standards

All projects must meet these standards:

### 1. Type Safety (Required)
- ✅ MyPy in strict mode: zero type errors
- ✅ All functions have complete type hints
- ✅ `py.typed` marker file present

```bash
make type-check  # Must pass
```

### 2. Code Quality (Required)
- ✅ Ruff linting: no errors
- ✅ Ruff formatting: consistent style
- ✅ Line length: 100 characters max

```bash
make lint        # Must pass
make format      # Auto-fixes
```

### 3. Testing (Required)
- ✅ 80% code coverage minimum
- ✅ All tests pass
- ✅ Property-based tests with Hypothesis

```bash
make test        # Must pass with ≥80% coverage
```

### 4. Security (Required)
- ✅ Bandit: no high-severity issues
- ✅ No secrets in code

```bash
make security    # Must pass
```

### 5. Documentation (Required)
- ✅ Google-style docstrings for all public APIs
- ✅ README with installation and usage
- ✅ PROJECT_SPECIFICATION.md addressed

---

## 📊 Assessment Criteria

### Technical Implementation (40%)
- Correct implementation of domain-specific algorithms
- Code correctness and edge case handling
- Performance and scalability
- Innovation and creativity

### Software Engineering (30%)
- Code quality and organization
- Test coverage and quality
- Type safety and documentation
- Git workflow and commit quality

### Domain Knowledge (20%)
- Understanding of problem domain
- Appropriate use of domain techniques
- Validation against known results
- Literature review and references

### Presentation (10%)
- Live demonstration
- Technical report quality
- Ability to explain design decisions
- Responses to questions

---

## 🔧 CI/CD Configuration

Add `.github/workflows/ci.yml` to each template:

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
        python-version: ["3.10", "3.11", "3.12"]

    steps:
    - uses: actions/checkout@v4

    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v5
      with:
        python-version: ${{ matrix.python-version }}

    - name: Install uv
      run: pip install uv

    - name: Install dependencies
      run: uv sync --extra dev

    - name: Lint with Ruff
      run: uv run ruff check src tests

    - name: Check formatting
      run: uv run ruff format --check src tests

    - name: Type check with MyPy
      run: uv run mypy src

    - name: Run tests
      run: uv run pytest tests --cov=src --cov-report=xml --cov-fail-under=80

    - name: Upload coverage
      uses: codecov/codecov-action@v3
      if: matrix.os == 'ubuntu-latest' && matrix.python-version == '3.11'
```

---

## 📝 Grading Rubric

### Code Quality (30 points)
- [ ] 10 pts: All quality checks pass (ruff, mypy, tests)
- [ ] 10 pts: Test coverage ≥80% with meaningful tests
- [ ] 5 pts: Clean code organization and structure
- [ ] 5 pts: Comprehensive documentation

### Technical Implementation (40 points)
- [ ] 20 pts: Core features implemented correctly
- [ ] 10 pts: Edge cases and error handling
- [ ] 5 pts: Performance and efficiency
- [ ] 5 pts: Innovation and extensions

### Domain Knowledge (20 points)
- [ ] 10 pts: Correct application of domain concepts
- [ ] 5 pts: Validation against known results
- [ ] 5 pts: Literature review and references

### Presentation (10 points)
- [ ] 5 pts: Live demonstration
- [ ] 3 pts: Technical report
- [ ] 2 pts: Q&A responses

**Total: 100 points**

---

## 🐛 Common Issues and Solutions

### Issue: "MyPy reports many errors"
**Solution**: Students should start with less strict MyPy config initially:
```toml
[tool.mypy]
strict = false  # Start with false
warn_return_any = true
disallow_untyped_defs = false  # Enable gradually
```

### Issue: "Tests fail with import errors"
**Solution**: Ensure virtual environment is activated:
```bash
source .venv/bin/activate  # Unix
.venv\Scripts\activate     # Windows
# Or use uv run pytest
```

### Issue: "Pre-commit hooks are too slow"
**Solution**: Skip heavy hooks during development:
```bash
git commit --no-verify
# But must pass before final submission
```

### Issue: "Coverage below 80%"
**Solution**: Identify uncovered lines:
```bash
make test
open htmlcov/index.html  # View detailed coverage report
```

---

## 📚 Additional Resources for Students

### Python Best Practices
- [Real Python](https://realpython.com/)
- [Python Type Hints](https://docs.python.org/3/library/typing.html)
- [Effective Python](https://effectivepython.com/)

### Testing
- [Pytest Documentation](https://docs.pytest.org/)
- [Hypothesis for Property-Based Testing](https://hypothesis.readthedocs.io/)

### Domain-Specific
- **Game Theory**: Axelrod's "Evolution of Cooperation"
- **Actuarial**: CAS/SOA exam materials
- **Finance**: Quantitative finance textbooks
- **Time Series**: Hyndman & Athanasopoulos "Forecasting"
- **ML**: "Hands-On Machine Learning" by Géron
- **Operations Research**: Winston "Operations Research"

---

## 🔒 Academic Integrity

### Allowed
- ✅ Consulting documentation and textbooks
- ✅ Discussing concepts with classmates
- ✅ Using AI assistants (must be logged in AI_LOG.md)
- ✅ Referencing open-source implementations (with attribution)

### Not Allowed
- ❌ Copying code from other students
- ❌ Using code without attribution
- ❌ Sharing your implementation with others
- ❌ Using AI to generate large code blocks without understanding

### AI Usage Policy
Students using AI assistants (ChatGPT, Claude, Copilot) must:
1. Create `AI_LOG.md` in repository root
2. Log each usage with:
   - Date and tool used
   - What was requested
   - How output was used/modified
   - Your understanding and learning

---

## 📞 Support

### Office Hours
Schedule regular office hours for:
- Template setup help
- Domain knowledge questions
- Debugging assistance
- Architecture discussions

### Discussion Forum
Set up course forum (Discord/Slack/Moodle) with channels:
- `#general` - General questions
- `#setup` - Installation and environment
- `#econgames`, `#simclt`, etc. - Project-specific
- `#showcase` - Students share progress

### FAQ Document
Maintain FAQ with common issues and solutions.

---

## 📅 Suggested Timeline

### Week 1-2: Project Selection & Setup
- Students choose template
- Fork/clone repository
- Set up development environment
- Read PROJECT_SPECIFICATION.md

### Week 3-4: Core Implementation
- Implement basic features
- Write initial tests
- Set up CI/CD

### Week 5-6: Advanced Features
- Complete all requirements
- Add extensions
- Reach 80% coverage

### Week 7: Documentation & Polish
- Write comprehensive docs
- Technical report
- Prepare presentation

### Week 8: Submission & Presentation
- Tag v1.0.0 release
- Publish to TestPyPI
- Live demo

---

## 🎯 Success Metrics

Track these metrics across all projects:

- Average test coverage percentage
- Number of type errors at submission
- CI/CD pass rate
- Lines of code per project
- Time to first successful CI run
- Student satisfaction survey

---

## 📦 Publishing to TestPyPI

Students should publish their packages:

```bash
# Install build tools
pip install build twine

# Build package
python -m build

# Upload to TestPyPI
python -m twine upload --repository testpypi dist/*

# Test installation
pip install --index-url https://test.pypi.org/simple/ package-name
```

---

## 🎓 Conclusion

These templates provide a solid foundation for teaching professional software engineering practices in a domain-specific context. Students will emerge with:

- Production-quality code skills
- Deep understanding of chosen domain
- Experience with modern Python tooling
- Portfolio-ready projects
- Confidence in software development

**Good luck with your course!**

---

*Questions? Contact: aleph@unil.ch*
