# New repo setup

## General

* For secrets, use environment variables in a .env file; maintain a set of default values in .env.sample
* You have access to github's `gh` cli tool. Use it for repo management and configuration, and anything else you might need it for, but always ask before any operations that might write to github

## Python projects

### Setup

* Use `uv` for package management; `uv venv` to set up a virtualenv
* After `uv init` be sure to remove `hello.py` cruft
* Always start by installing `rust-just` for project-specific commands and `pytest` for testing
* Then create a justfile with the first two commands, and consider the others:
  * `clean` - runs `ruff` and `isort` with autofixing options
  * `test` - runs tests
  * `dev` - starts up any servers in dev mode (e.g. with auto reloading)
  * `build` - creates assets, e.g. for a static site generator
*  Manage all one-off commands via just
  
### General usage

* For new functionality, write tests first, and confirm they fail as expected
* For new bugs, also write tests first
* When investigating bugs, consider temporarily adding debug print statements to help you track problems 
* Tests should be specific, named imperatively, and be arranged for legibility. For example, not too many tests in a module; each test should be a few lines long unless it's a smoketest or similar; fixtures should also be legible
* If there's more than one good way to approach writing a feature, ask me for my preference
* Do not write code which has fallbacks or other default values, unless asked. For example, never do bare excepts. As an example, if keys are missing in dicts, then allow the exception to propagate. In general, ALWAYS fail noisily, to maximise the amount of information available at runtime for debugging problems
* In general, don't use typing. Only use it when there's a clear and obvious justification.
* When writing code against things that are hard to test, such as third party APIs, also write smoketests that excercise an entire flow, using live tokens, and use them in debugging loops. However, exercise extreme caution about any test operations that might write to a production service; always stop and ask what you should do first, including suggesting obtaining read-only PATs for such tests (if possible)
