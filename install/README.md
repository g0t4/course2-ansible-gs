# How to install ansible?

There is no "right way." Pick what is familiar and works (i.e. to learn):

## I want simple...

#### 1. global install into site-packages
```bash
pip3 install ansible
```
- permission denied? try `--user`
- conflict with installed packages? try `venv`

#### 2. install into user site
```bash
pip3 install --user ansible
```
- check pip output for
  _WARNING: The scripts ... are installed in '/path/to/bin' which is not on PATH_

## I want to isolate my ansible installation...

#### 3. install into an explicit venv (virtual environment)
```bash
python3 -m venv .venv
source .venv/bin/activate # must run in each new shell, easy to forget
pip install ansible 
```
- FYI `pip` => `.venv/bin/pip`
  - `ansible(-*)` => `.venv/bin/ansible(-*)` 
- [`venv` docs](https://docs.python.org/3/library/venv.html#creating-virtual-environments)

#### 4. install into an implicit venv (pipx managed)
```bash
pipx install --include-deps ansible
```
- Without `--include-deps` you'll only see the `ansible-community` command
  - Ansible is split into two packages: `ansible` + `ansible-core`. `ansible` depends on `ansible-core`
  - `ansible` package only has the `ansible-community` command
  - `ansible-core` has the rest of the `ansible(-*)` commands 
  - `--include-deps` tells `pipx` to install commands from `ansible-core` too (all dependencies actually)
- [`pipx` docs](https://pypa.github.io/pipx/) 

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

## I'd rather use my OS package manager...
- See the [Ansible distro install docs for commands to copy/paste](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)

## Validate ansible works
```sh
ansible --version
```
- `command not found` => find where `ansible(-*)` commands are installed and add to your path or otherwise fix

