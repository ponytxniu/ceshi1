# Welcome to Reflex contributing guide! 🥳

## Getting started

To navigate our codebase with confidence, see [Reflex Docs](https://pynecone.io/docs/getting-started/introduction) :confetti_ball:. 

### Discussions

- Have a question? Want to discuss a feature? [Start a discussion](https://github.com/pynecone-io/pynecone/discussions)

    We welcome any discussions and questions. We want to make sure that Reflex is the best it can be, and we can't do that without your help.

### Issues

* #### Create a new issue

    If you spot a problem with anything in Reflex feel free to create an issue. Even if you are not sure if its a problem with the framework or your own code, create an issue and we will do our best to answer or resolve it.

* #### Solve an issue

    Scan through our [existing issues](https://github.com/pynecone-io/pynecone/issues) to find one that interests you. You can narrow down the search using `labels` as filters. As a general rule, we don’t assign issues to anyone. If you find an issue to work on, you are welcome to open a PR with a fix. Any large issue changing the compiler of Reflex should brought to the Reflex maintainers for approval

Thank you for supporting Reflex!🎊

## 💻 How to Run a Local Build of Reflex 
Here is a quick guide to how the run Reflex repo locally so you can start contributing to the project.

First clone Reflex:
``` bash
git clone https://github.com/pynecone-io/pynecone.git
```

Navigate into the repo:
``` bash
cd reflex
```

Install poetry version >= 1.4.0 and add it to your path (see [Poetry Docs](https://python-poetry.org/docs/#installation) for more info).

Install your local Reflex build:
``` bash
poetry install
```

Now create an examples folder so you can test the local Python build in this repository:
``` bash
mkdir examples
cd examples
```

Create a project in this folder can be named anything but for the sake of the directions we'll use `example`:
``` bash
mkdir example
cd example
```

Now Init/Run
``` bash
poetry run reflex init
poetry run reflex run
```

All the changes you make to the repository will be reflected in your running app.
* We have the examples folder in the .gitignore, so your changes in reflex/examples won't be reflected in your commit.

## 🧪 Testing and QA

Any feature or significant change added should be accompanied with unit tests.

Within the 'test' directory of Reflex you can add to a test file already there or create a new test python file if it doesn't fit into the existing layout.

What to unit test?
- Any feature or significant change that has been added.
- Any edge cases or potential problem areas.
 -Any interactions between different parts of the code.


## ✅ Making a PR

Once you solve a current issue or improvement to Reflex, you can make a pr, and we will review the changes. 

Before submitting, a pull request, ensure the following steps are taken and test passing.

In your `reflex` directory run make sure all the unit tests are still passing using the following command.
This will fail if code coverage is below 80%.
``` bash
poetry run pytest tests --cov --no-cov-on-fail --cov-report= 
```
Next make sure all the following tests pass. This ensures that every new change has proper documentation and type checking.
``` bash
poetry run ruff check .
poetry run pyright reflex tests
find reflex tests -name "*.py" -not -path reflex/reflex.py | xargs poetry run darglint
```
Finally, run `black` to format your code.
``` bash
poetry run black reflex tests
```

Consider installing git pre-commit hooks so Ruff, Pyright, Darglint and Black will run automatically before each commit.
Note that pre-commit will only be installed when you use a Python version >= 3.8.
``` bash
pre-commit install
```

That's it you can now submit your pr. Thanks for contributing to Reflex!
