Setup & get started with pyenv
You can follow the steps below for installing on macOS. I’m using Homebrew, but see the pyenv documentation for alternative installation methods.

# Install pyenv.
brew install pyenv

# Add pyenv initializer to shell startup script.
echo -e '\nif command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi' >> ~/.bash_profile

# Reload your profile.
source ~/.bash_profile
With pyenv installed, you can install any python version that you would like. Below I am installing some python versions. Depending on which directory you’re in, pyenv will point to your specified python version.

# See all available python installations.
pyenv install --list

# Install some python versions.
pyenv install  3.7.6
pyenv install  2.7.17
pyenv install  3.8.1

# See all python installations that you have installed.
pyenv versions

# Set the default/global from one of the python versions.
pyenv global 3.8.1

# In the current directory, set the python version. This creates the file .python-version.
pyenv local 3.9.10

# To see which python is currently being used.
pyenv version

poetry
poetry is a packaging and dependency manager. It resolves your library dependencies, and can build and publish your project to be distributed on your private pypi repository. In the beginning of December 2019, version 1.0.0 was finally released!

The main file of your poetry project is the pyproject.toml file. Define the requirements, the dev-requirements and project metadata in this file. poetry uses the .toml file to resolve the dependencies of your defined requirements, and creates the poetry.lock file. Then poetry creates a virtual environment and installs everything from the .lock file.

(Some alternatives to poetry for virtual environments are virtualenv, conda, venv or pipenv. I’ve used them all, especially pipenv. However, I believe that `poetry is superior!)

Setup poetry
As of writing, poetry is not yet available on Homebrew. Follow the steps below for installing it.

# Install poetry via curl
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python

# Add poetry to your shell
export PATH="$HOME/.poetry/bin:$PATH"

# For tab completion in your shell, see the documentation
poetry help completions

# Configure poetry to create virtual environments inside the project's root directory
poetry config virtualenvs.in-project true