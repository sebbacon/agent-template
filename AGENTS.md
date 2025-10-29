# New repo setup

## Python projects
### Setup
* Use `uv` for package management; `uv venv` to set up a virtualenv
* After `uv init` be sure to remove `hello.py` cruft
* Always start by installing `rust-just` for project-specific commands and `pytest` for testing
* Then create a justfile with the first two commands, and consider the others:
  * `clean` - runs `ruff` and `isort` with autofixing options
  * `test` - runs tests
  * `dev` - starts up any servers in dev mode (e.g. with auto reloading)
  * `build` - creates assets, e.g. for a static site generator
 
### General usage
* For new functionality, write tests first, and confirm they fail as expected
* For new bugs, also write tests first
* Tests should be specific, named imperatively, and be arranged for legibility. For example, not too many tests in a module; each test should be a few lines long unless it's a smoketest or similar; fixtures should also be legible
* If there's more than one good way to approach writing a feature, ask me for my preference
