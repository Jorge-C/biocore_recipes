# biocore_recipes
Conda recipes for biocore projects.

# Setting up the build environment

We follow the instructions in the [conda
docs](http://conda.pydata.org/docs/build_tutorials/pkgs.html#tutorial-basic-tutorial-for-building-a-conda-package),
but here's an overview of the process.

Since we have conda already installed, we update it and use it to
install `conda-build`. In linux, we also install `patchelf`

```
$ conda update conda
$ conda install conda-build
$ conda install patchelf
```

# Creating recipes


Most recipes were created using the skeleton command

`conda skeleton pypi pckg`

but they usually require some manual edits (setting requirements
versions, some tests commands...).

To keep them up to date it should be enough to update their
dependencies and version string, but it'd be nice if that was
automatic... They can also be built from git tags or track branches,
but here we're currently building them from PyPI releases (or a master
branch).

# Building packages

First, let's make sure everything is updated when building packages:

```
$ conda update conda conda-build patchelf
```

```
$ conda build qiime
```

# Sharing packages

If registered in binstar (like PyPI, for conda builds) and logged in
(`$ binstar login`), the build command will give, if successful, a
command to update the binary package. It can be done automatically by
configuring `conda config --set binstar_upload yes`.