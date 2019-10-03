# Use at your own risk!

Why are there 2 scripts to remove resources?

The first script `jnrmor` removes orphaned resources from the database and the meta data files for those resources from the sync target. ~~Due to an error in the Joplin API, the actual resources are not deleted on the sync target.
There's where script `jnclnst` comes to the rescue.~~

The default locations for the config files are the path of the script and your home directory. These locations will be shown with the option `--help`.

## Requirements

bash version 4 is required for `jnclnst`. All scripts use getopt to parse the arguments. Unfortunately the getopt that comes with macOS is a useless piece of shit and can't be used in any useful manner.

### macOS

The best way to install proper versions of `bash` and `getopt` is to either use MacPorts or brew. Make sure the binaries are in the PATH before `/bin` and `/usr/bin`.

#### MacPorts

```
sudo port install bash
sudo port install getopt
```

#### brew

```
brew install bash
brew install gnu-getopt
```

## `jnrmor` - remove orphaned resources in Joplin

```
usage: jnrmor [-c CONFIGFILE] [-f] [-q|--quiet] [-n|--dry-run] [-d|--debug] [-V|--version] [-h] [--help]

       -c CONFIGFILE
           use CONFIGFILE, instead of searching the default locations
           The first file found is used.

       -f
           run without confirmation

       -q, --quiet
           do not print informational messages
           (errors will be shown)

       -n, --dry-run
           only show orphaned resources (do not actually delete them)
           implies -f

       -d, --debug
           print debug information

       -V, --version
           version information

       -h
           usage information

       --help
           this help
```

If you rather use a perl script, head over [here](https://github.com/sciurius/perl-Joplin-API). You can use the script `listnotes.pl` with the option `--weed`.

## `jnclnst` - clean sync target (remove orphaned resources from sync target)

This script is no longer needed. A fix was added to Joplin a while back. It’s only here for reference and for people who still use an old Joplin version.
It doesn’t hurt to run the script, it just won’t find anything to remove anything anymore.

```
usage: jnclnst [-c CONFIGFILE] [-f] [-q|--quiet] [-n|--dry-run] [-d|--debug] [-V|--version] [-h] [--help]

       -c CONFIGFILE
           use CONFIGFILE, instead of searching the default locations
           The first file found is used.

       -f
           run without confirmation

       -q, --quiet
           do not print informational messages
           (errors will be shown)

       -n, --dry-run
           only show orphaned resources (do not actually delete them)
           implies -f

       -d, --debug
           print debug information

       -V, --version
           version information

       -h
           usage information

       --help
           this help
```
