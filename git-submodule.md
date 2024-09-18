# `git submodule`

A _git submodule_ is a separate repository within a repository, i.e. it allows git repositories
to be nested within other separate repositories.

A `.gitmodules` file is used in the parent repository to manage the submodules.
A typical `.gitmodules` file looks like this:

```shell
[submodule "lib/submodule"]
    path = lib/submodule
    url = https://github.com/username/repository.git
```

## Add a submodule

```shell
cd /path/to/parent/repo
git submodule add https://github.com/username/repository.git lib/submodule
```

## List submodules in a repo

```shell
git submodule
git submodule status --recursive
ls -al lib/submodule
```

## Initialize and update a submodule

```shell
# git submodule update --init
git submodule update --init --recursive
```

## Commit the changes

```shell
git add .gitmodules lib/submodule
git commit -m "Add submodule: lib/submodule"
```
