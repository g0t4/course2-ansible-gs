# How to install ansible?

There is no "right way." Pick what is familiar and works (i.e. to learn)... _Note: most of these techniques apply to installing any python package. Thus, links are mostly to python docs to elaborate for those of you that are curious!_

## I want simple...

#### 1. install into global site-packages
```bash
pip3 install ansible
```
- permission denied? try `--user`
- conflict with installed packages? try `venv`

#### 2. install into user site
```sh
pip3 install --user ansible
```
- check pip output for
  _WARNING: The scripts ... are installed in '/path/to/bin' which is not on PATH_
  - Fix by running one of these:
    ```sh
    PATH="/path/to/bin:${PATH}" # check first (versus current path directories)
    PATH="${PATH}:/path/to/bin" # OR, check last
    ```
    - Add to shell startup files: i.e. ~/.zprofile (zsh) or ~/.bash_profile:
- user site: [docs](https://packaging.python.org/en/latest/tutorials/installing-packages/#installing-to-the-user-site) / [PEP 370](https://peps.python.org/pep-0370/)

## I'd rather use my OS package manager...

- See the [Ansible distro install docs for commands to copy/paste](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)
- On macOS, homebrew installs ansible with `pip` into a `virtual environment`, transparently.
```sh
brew install ansible
```

## I want to isolate my ansible installation...

#### 3. install into an explicit venv (virtual environment)
```bash
python3 -m venv .venv
source .venv/bin/activate # must run in each new shell, easy to forget
pip install ansible 
```
- FYI `pip` => `.venv/bin/pip`
  - `ansible(-*)` => `.venv/bin/ansible(-*)` 
- `venv`: [docs](https://docs.python.org/3/library/venv.html) / [PEP 405](https://peps.python.org/pep-0405) / [rationale](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments)
  - FYI if you're curious... [PEP 704 - Proposal - default pip to require using venv(s)](https://peps.python.org/pep-0704/)

#### 4. install into an implicit venv (pipx managed)
```bash
pipx install --include-deps ansible
```
- Without `--include-deps` you'll only see the `ansible-community` command
  - Ansible is split into two packages: `ansible` + `ansible-core`. `ansible` depends on `ansible-core`
  - `ansible` package only has the `ansible-community` command
  - `ansible-core` has the rest of the `ansible(-*)` commands 
  - `--include-deps` tells `pipx` to install commands from `ansible-core` too (all dependencies actually)
- [installing standalone commands](https://packaging.python.org/en/latest/guides/installing-stand-alone-command-line-tools)
- [`pipx` docs](https://pypa.github.io/pipx)

## I have multiple python installs...

With multiple python versions (interpreters) installed, `pip`/`pip3` is ambiguous. Which version of python does it **link** to? Worse yet, updating `pip` can change what `pip`/`pip3` is **linked** to! To avoid this...

#### 5. set desired interpreter with pip's new --python option
```bash
pip3 --python /path/to/python3 install [--user] ansible
```
- [`--python` docs](https://pip.pypa.io/en/stable/topics/python-option/)

#### 6. use desired interpreter to run pip
```bash
python3 -m pip install [--user] ansible
```

## Validate ansible works
```sh
ansible --version
```
- `command not found` => find where `ansible(-*)` commands are installed and add to your path or otherwise fix

