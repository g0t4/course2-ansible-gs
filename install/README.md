# How to install ansible?

There is no "right way." Pick what is familiar and works (i.e. to learn):

## I want simple...

```bash
# 1. global install into site-packages
pip3 install ansible
```
- permission denied? try `--user`
- conflict with installed packages? try `venv`

```bash
# 2. install into user site
pip3 install --user ansible
```
- check pip output for
  _WARNING: The scripts ... are installed in '/path/to/bin' which is not on PATH_

## I want to isolate my ansible installation...

```bash
# 3. install into explicit venv
python3 -m venv .venv
source .venv/bin/activate # must run in new shell
pip --version # ensure activated! look at `from`
pip install ansible 
```
- `pip` => `.venv/bin/pip`
- `ansible(-*)` => `.venv/bin/ansible(-*)` 
- [`venv` docs](https://docs.python.org/3/library/venv.html#creating-virtual-environments)

```bash
# 4. install into implicit venv (pipx managed)
pipx install --include-deps ansible
```
- without `--include-deps` you'll only see `ansible-community` command, ansible-core has most `ansible(-*)` commands and is a dep of `ansible` package (hence `--include-deps`)
- [`pipx` docs](https://pypa.github.io/pipx/) 

## I have multiple python installs...

With multiple python versions (interpreters) installed, `pip` is ambiguous. Which version of python does it **link** to? Likewise for `pip3`. Worse yet, updating `pip` can change what `pip`/`pip3` is **linked** to! Use the following to...

```bash
# 5. set desired interpreter with pip's new --python option
pip3 --python /path/to/python3 install [--user] ansible
```
- [`--python` docs](https://pip.pypa.io/en/stable/topics/python-option/)

```bash
# 6. use desired interpreter to run pip
python3 -m pip install [--user] ansible
```

## Validate ansible works

```sh
ansible --version
```
- `command not found` => find where `ansible(-*)` commands are installed and add to your path or otherwise fix