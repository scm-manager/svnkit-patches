# SCM-Manager patches for SVNKit

This repository contains pathes for the usage of
[SVNKit](http://svnkit.com/) in [SCM-Manager](https://scm-manager.org/).
These patches can be applied using [guilt](https://github.com/jeffpc/guilt).

## How To

To apply these patches, first clone the forked repository of SVNKit:

```
git clone git@github.com:scm-manager/svnkit.git
cd svnkit
```

Then clone this repository in the patches directory in `.git`:

```
git clone git@github.com:scm-manager/svnkit-patches.git .git/patches
```

Finally apply the patches with guilt:

```
guilt push -a
```

__Do not push these applied patches to the svnkit repository!__

