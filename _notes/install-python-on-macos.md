---
title: Installing Python on macOS
date: 2023-10-24
---

- Don't use Homebrew Python
  - https://justinmayer.com/posts/homebrew-python-is-not-for-you/
- Instead, use [pyenv](https://github.com/pyenv/pyenv) and [virtualenv](https://github.com/pyenv/pyenv-virtualenv)
  - https://www.timescale.com/blog/jupyter-notebook-tutorial-setup-python-and-jupyter-notebooks-macos/


## Steps

1. Install pyenv and pyenv-virtualenv:
   ```bash
   brew install pyenv
   brew install pyenv-virtualenv
   ```
1. Add the following to `~/.bashrc`:
   ```
   eval "$(pyenv init -)"
   ```


