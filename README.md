# AION Web3.py

This is a fork of the original Ethereum web3.py libraries with changes specific to the AION blockchain.

* Python 3.5+ support

Read more in the [documentation on ReadTheDocs](http://web3py.readthedocs.io/). [View the change log on Github](docs/releases.rst).


### Testing Setup

During development, you might like to have tests run on every file save.

Show flake8 errors on file change:

```sh
# Test flake8
when-changed -v -s -r -1 web3/ tests/ ens/ -c "clear; flake8 web3 tests ens && echo 'flake8 success' || echo 'error'"
```

You can use `pytest-watch`, running one for every Python environment:

```sh
pip install pytest-watch

cd venv
ptw --onfail "notify-send -t 5000 'Test failure ⚠⚠⚠⚠⚠' 'python 3 test on web3.py failed'" ../tests ../web3
```

Or, you can run multi-process tests in one command, but without color:

```sh
# in the project root:
pytest --numprocesses=4 --looponfail --maxfail=1
# the same thing, succinctly:
pytest -n 4 -f --maxfail=1
```

#### How to Execute the Tests?

1. [Setup your development environment](https://github.com/ethereum/web3.py/#developer-setup).

2. Execute `tox` for the tests

There are multiple [components](https://github.com/ethereum/web3.py/blob/master/.travis.yml#L53) of the tests. You can run test to against specific component. For example:

```sh
# Run Tests for the Core component (for Python 3.5):
tox -e py35-core

# Run Tests for the Core component (for Python 3.6):
tox -e py36-core
```

If for some reason it is not working, add `--recreate` params.

`tox` is good for testing against the full set of build targets. But if you want to run the tests individually, `py.test` is better for development workflow. For example, to run only the tests in one file:

```sh
py.test tests/core/gas-strategies/test_time_based_gas_price_strategy.py
```
