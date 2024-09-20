# `git subtree`

`git subtree` is good for organising many sub-directories within a single repository.
While keeping the contents and commit history of all the sub-directories, it allows us
to maintain (or later extract) a completely separate repository for each sub-directory
at some other (remote) location.

This approach is especially beneficial for projects requiring close integration without
the overhead of submodule management.

`git subtree` is okay for simple use cases. However, for complex use cases like
some subtree directory having its own submodules (i.e. has `.gitmodules` file), it
can be difficult to work with.

If you want to run the sub-directory project independently, then you may face issues
since most projects assume independent git history. For example, running `forge build`
in a sub-directory project fails as it's unable to find necessary git submodules somehow.

## Create a "local remote" from a local git repo

```shell
cd /Users/abraj/dev/archive/learn-solidity/.local/01
cp -R . ../01-bkp/  # take a backup (untested command)
git init --bare
# delete the `bare` repo and restore backup
```

## Add new subtree (repo) from a "local remote"

```shell
git subtree add --prefix=lib/01 /Users/abraj/dev/archive/learn-solidity/.local/01 main
# git subtree pull --prefix=lib/01 /Users/abraj/dev/archive/learn-solidity/.local/01 main
# git subtree push --prefix=lib/01 /Users/abraj/dev/archive/learn-solidity/.local/01 main
```

## Add new subtree (repo) from a GitHub repo

```shell
git subtree add --prefix=lib/03 https://github.com/abraj/nextjs-starter.git main
```

**NOTE:** Adding the subtree as a _remote_ allows us to shorten the `git subtree pull` command.

```shell
git remote add nextjs-demo https://github.com/abraj/nextjs-demo.git
git subtree add --prefix lib/nextjs-demo nextjs-demo main

# And, later..
git fetch nextjs-demo main
git subtree pull --prefix lib/nextjs-demo nextjs-demo main
```

The same holds true for contributing back to the _upstream_.

```shell
git remote add nextjs-demo git@github.com:abraj/nextjs-demo.git
git subtree push --prefix=lib/nextjs-demo nextjs-demo main
```

## Extract subtree-repo into a tracking branch

```shell
git subtree split --prefix=lib/01 --branch=repo-01
git push origin repo-01
git branch -d repo-01
git branch -d -r origin/repo-01
```

## Restore a subtree-repo from its tracking branch

```shell
cd .local && git clone https://github.com/abraj/learn-solidity.git --branch repo-01 --single-branch
# mv learn-solidity 01 && cd 01
# git pull origin repo-01
```
