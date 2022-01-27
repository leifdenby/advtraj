# Developing advtraj

To work on the `advtraj` codebase yourself you will want to know 1) how to get
and install a local copy of `advtraj`, 2) how to run the advtraj tests locally
and 3) how to contribute your changes back to the community. We've covered all
these steps below - welcome in the advtraj community! :)

Here's a quick TLDR version if you're already familiar with github:

```bash
# Create a fork of the `advtraj` repository on github by clicking the following
# link: https://github.com/ParaConUK/advtraj/fork)

# clone locally your fork of advtraj on github
git clone https://github.com/<your-github-username>/advtraj/

# install this local copy with pip and additionally install the development
# tools
pip install -e ".[dev]"

# install pre-commit and its git hooks to automatically have your code linted
# when you do a git commit (this ensures that we pick up simple mistakes and
# keep the formatting clean)
pre-commit install

# create a branch for your fix/feature
git checkout -b my-new-feature

# make any modifications you want, make sure to add a test if you're fixing a
# bug and the run the tests
python -m pytest .

# apply code cleanup with black, then commit these changes locally with git
black .
git add .
git commit

# push these changes to your fork on github (providing the name of the branch
# you want to push)
git push origin my-new-feature

# create a pull-request on github to pull in your branch by clicking the link
# the output from the last command, or go to
# https://github.com/ParaConUK/advtraj/compare
```

## Installing from a local copy

When you're making modifications to the advtraj codebase you will want to
install this local copy with `pip` instead of installing from github or pypi.
First you will want to [create your own fork]() of advtraj on github.

```bash
git clone https://github.com/<your-github-username>/advtraj/
```

You can then install with `pip` using the following command (the `-e`-flag
ensures that pip will pick up any changes you make to the source directory)

```
pip install -e ".[dev]"
```

This will install the `advtraj` codebase into your current python environment
together with some development tools (you can see which by having a look in
`setup.py`). For automatic code cleanup you will need to setup `pre-commit` by
running

```bash
pre-commit install
```

pre-commit hooks into git so that it is automatically run each time you do a
commit.


## Adding features and fixing bugs

Modifying the advtraj codebase to add features and fix bugs follows the
common process of branch, fix, test and pull-request. Once you've cloned your
fork of advtraj locally and installed it with pip (see above) you can start
making your changes!

Start by creating a branch for you feature/fix:

```bash
git checkout -b my-new-feature
```

Then make any changes you'd like and commit them locally:

```bash
git add .
git commit
```

To test that your new feature doesn't break anything you can run the tests
locally (these will also be run automatically on github, see more details on
testing below)

```bash
python -m pytest .
``

(don't worry about making individual git commits, we can squash them all
together before merging into the main repository!)`

Finally, when you're happy with your changes you need to push your branch to
github and make a pull-request. The pull-request will tell the rest of the
advtraj community that you have a change you'd like to get added to the
community version of advtraj

```bash
git commit -m 'apply black'
git push origin my-new-feature
```

The last command will give you a link to where you can create a pull-request on
github, otherwise you can also go to
https://github.com/EUREC4A-UK/advtraj/compare


## Testing advtraj

`advtraj` is automatically checked on github with tests that reside in `tests/`.
These are run automatically on all pull-requests against the git
repository at https://github.com/EUREC4A-UK/advtraj and can be run locally
with `pytest` from the root of the repository:

```bash
pip install pytest
python -m pytest
```

It is useful to have a `ipdb`-debugger open up inline on failing
tests. This can be achieved by first installing `ipdb` and setting the
`PYTEST_ADDOPPS` environment variable:

```bash
export PYTEST_ADDOPTS='--pdb --pdbcls=IPython.terminal.debugger:Pdb'
```
