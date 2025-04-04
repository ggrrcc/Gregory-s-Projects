# Setting Up pyenv on Debian

## 1. Install Dependencies
necessary build dependencies:

```sh
sudo apt update && sudo apt install -y \
    make build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl \
    llvm libncursesw5-dev xz-utils tk-dev \
    libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

## 2. Install pyenv
official install script:

```sh
curl https://pyenv.run | bash
```

## 3. Update Shell Configuration
Add the following lines to your shell profile (e.g., `~/.bashrc` or `~/.zshrc`):

```sh
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

Then, reload your shell configuration:

```sh
exec $SHELL
```

## 4. Optional: Verify Installation
Check:

```sh
pyenv --version
```

## 5. Install Python Versions
Install Python 3.9.21:

```sh
pyenv install 3.9.21
pyenv global 3.9.21
```

## 6. Check Active Python Version
Verify that `pyenv` is managing Python correctly:

```sh
python --version
```

---
