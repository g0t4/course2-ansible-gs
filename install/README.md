# How to install ansible?

There is no "right way." Pick what is familiar and works (i.e. to learn):

```bash

# 1. global install into site-packages:
pip3 install ansible
# easiest, but can be problematic (i.e. permissions issue, conflict with installed packages, etc)
  # 2. install into user site:
  pip3 install --user ansible
  # watch for WARNING: The scripts ... are installed in '/path/to/bin' which is not on PATH.

# 3. install into explicit venv
python3 -m venv .venv
source .venv/bin/activate # must run each time you open a new shell
pip install ansible # installs into .venv (FYI pip => .venv/bin/pip)
# https://docs.python.org/3/library/venv.html#creating-virtual-environments

# 4. install into "implicit venv" (pipx manages the venv)
pipx install --include-deps ansible
# --include-deps is needed to install all ansible-* commands (ansible-core has most of the commands)
# https://pypa.github.io/pipx/

# 5. install with explicit python interpreter...
  # ... via pip's new --python option
    pip3 --python /path/to/python3 install [--user] ansible
    # https://pip.pypa.io/en/stable/topics/python-option/
  # ... via desired interpreter running pip
    python3 -m pip install [--user] ansible

```

## validate ansible works

```sh
ansible --version
# command not found => is the bin dir for ansible in your path?
```
