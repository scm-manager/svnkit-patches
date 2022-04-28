# SCM-Manager patches for SVNKit

This repository contains pathes for the usage of
[SVNKit](http://svnkit.com/) in [SCM-Manager](https://scm-manager.org/).
These patches can be applied using [guilt](https://github.com/jeffpc/guilt).

## How To ...

### Apply Patches

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

### Update and Create New Patches

Set `master` branch of svnkit repository to new base version:

```
git reset --hard <new sha2 hash>
```

Apply all patches:

```
guilt push -a
```

If a patch fails, force push it:

```
guilt push -f
```

Fix failed files (mind all `.re` files containing failed patches)

Refresh patch:

```
guilt refresh
```

Repeat for missing patches

If you want to create new patches, just do so:

```
guilt new <new patch name>
```

To create a new version, drop the old release patch and create a new one:

```
guilt delete <old version>
mvn versions:set -DnewVersion=<new version> -DgenerateBackupPoms=false
guilt refresh
```

Add new patch files, but __do not commit status file__.

### Build

To build the patched version of SVNKit, set your credentials for packages.scm-manager.org in `~/.gradle/gradle.properties`:

```
packagesScmManagerUsername=
packagesScmManagerPassword=
```

To install the version to the local maven repository, call

```
./gradlew install
```

### Run tests

Please run the tests from https://github.com/scm-manager/svn-server-spec

