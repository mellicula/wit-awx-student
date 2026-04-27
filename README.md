# WIT x Airwallex — Testing Workshop

A hands-on workshop for learning test-driven development (TDD) and testing best practices. You'll write tests for a small financial management suite and compete on a live leaderboard.

## What You're Testing

The `src/` directory contains four modules:

| Module | Description |
|--------|-------------|
| `currency.py` | Currency conversion across 8 currencies (AUD, USD, EUR, GBP, JPY, SGD, CNY, HKD) |
| `wallet.py` | Multi-currency wallet with deposits, withdrawals, and transfers |
| `expense.py` | Expense tracking with 6 categories (food, transport, accommodation, entertainment, shopping, other) |
| `budget.py` | Budget management and spend analysis |

## Getting Started

**Prerequisites:** Python 3.x

**Install dependencies:**
```bash
pip install -r requirements.txt
```

**Run the interactive CLI:**
```bash
python cli.py
```

This launches a menu-driven app where you can explore all four modules — wallet, expenses, budget, and currency conversion. Note: all data resets when you exit.

**Run your tests:**
```bash
bash run_tests.sh
```

This runs pytest with coverage reporting and posts your score to the leaderboard.

You can also run pytest directly:
```bash
python -m pytest --cov=src --cov-report=term-missing -v
```

## Your Task

Write tests in `tests/` that cover all four modules. Aim for comprehensive coverage — happy paths, edge cases, error handling, and validation.

`tests/test_example.py` contains six example tests to show you the expected pattern:

```python
# Arrange
wallet = Wallet()

# Act
wallet.deposit(100, "AUD")

# Assert
assert wallet.get_balance("AUD") == 100
```

## Workshop Modes

**Workshop mode** — the default. Your score is based on code coverage: how much of `src/` your tests exercise.

**Reveal mode** — activated by the workshop facilitator. The leaderboard serves broken versions of the source files, your tests run against them, and your score reflects how many bugs you catch (out of 4). Your original source files are restored automatically after each run.

## Project Structure

```
wit-awx-student/
├── src/
│   ├── currency.py
│   ├── wallet.py
│   ├── expense.py
│   └── budget.py
├── tests/
│   └── test_example.py   # Example tests — start here
├── cli.py                # Interactive CLI for exploring the modules
├── run_tests.sh          # Test runner + leaderboard integration
├── pytest.ini
└── requirements.txt
```

## Tips

- Read the source files before writing tests — understand what each function does and what errors it raises.
- Use `pytest.raises` to test that invalid inputs raise the right exceptions.
- The `InsufficientFundsError` in `wallet.py` is a custom exception worth testing explicitly.
- More test coverage in workshop mode → higher score. More bugs caught in reveal mode → higher score.
