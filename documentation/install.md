#  <a name="top"></a> VADR installation instructions

* [Installation using `vadr-install.sh`](#install.sh)
  * [Installing Inline and LWP if installation fails](#inline)
* [Setting environment variables](#environment)
* [Verifying successful installation](#tests)
* [Further information](#further)

---
## VADR installation using the `vadr-install.sh` script <a name="install"></a>

The file `vadr-install.sh` is an executable file for installing VADR
and its dependencies. That file is located online at github.
To install the latest version of VADR download this file:

https://raw.githubusercontent.com/nawrockie/vadr/master/vadr-install.sh

To download any specific release/version, for example version 1.0 download
the corresponding `vadr-install.sh` file for that release/version
(prior to version 1.0, the name of the installation script was
`install.sh`, not `vadr-install.sh`):

https://raw.githubusercontent.com/nawrockie/vadr/1.0/vadr-install.sh

Copy the `vadr-install.sh` file into the directory in which you want
to install VADR. A good name for that directory is
`vadr-install-dir`. Then move into that directory and run one of the
following two commands depending on whether you are installing on a
Linux or Mac/OSX system:

```
sh ./vadr-install.sh linux
```

OR

```
sh ./vadr-install.sh macosx
```
The `linux` or `macosx` argument controls (only) the type of infernal
and blast executable files that will be installed.

The `vadr-install.sh` command will create several directories in the
current directory.  It will download and install VADR and the required
module libraries [sequip](https://github.com/nawrockie/sequip),
[Bio-Easel](https://github.com/nawrockie/Bio-Easel), as well as the
binary executables of [Infernal](http://eddylab.org/infernal/) and the
NCBI BLAST package (for either Linux or Mac/OSX).

The installation requires that you have the perl Inline module
installed on your system. If not, the installation script will
fail. If this happens, read [this](#inline).

When `vadr-install.sh` is finished running it will print important
instructions to the screen that explain how to modify your environment
variables so that you can run the VADR scripts, as discussed next.

---
### If installation fails because the `Inline` or `LWP` perl modules are not installed...<a name="inline"></a>

The perl `Inline` and `LWP` modules must be installed prior to installation. You 
can install `Inline` using `cpan` with two commands:

`cpan install Inline`

`cpan install Inline::C`

Similarly, you can install `LWP` with:

`cpan install LWP`

`cpan install LWP::Simple`

However, for Mac/OSX these commands may not work if you have
not installed the "Command line tools for Xcode" or "XCode" packages.
You can download Xcode from the Mac App Store for free.

---

## Setting VADR environment variables <a name="environment"></a>

As mentioned above, when you run `vadr-install.sh`, instructions will be
output about how to change your environment variables so that you can
run the VADR scripts. Those instructions are also included below for
reference, but without the actual path to where you ran `vadr-install.sh`
(below it is replaced with `<full path to directory in which you ran
vadr-install.sh>`)

---
### Note to internal NCBI users <a name="ncbi"></a>

Contact Eric Nawrocki (eric.nawrock@nih.gov) to find out the
path to the centrally installed copy of VADR at NCBI
(`<ncbi-vadr-install-dir>`).

Then, to set up your environment variables, follow the instructions
below but replace: `<full path to directory in which you ran
vadr-install.sh>` with `<ncbi-vadr-install-dir>`

---

### Instructions for setting environment variables output by `vadr-install.sh`

```
The final step is to update your environment variables.
(See
https://github.com/nawrockie/vadr/blob/master/documentation/install.md
for more information.)

If you are using the bash or zsh shell (zsh is default in MacOS/X as
of v10.15 (Catalina)), add the following lines to the end of your 
'.bashrc' or '.zshrc' file in your home directory:

export VADRINSTALLDIR=<full path to directory in which you ran vadr-install.sh>
export VADRSCRIPTSDIR="$VADRINSTALLDIR/vadr"
export VADRMODELDIR="$VADRINSTALLDIR/vadr-models"
export VADRINFERNALDIR="$VADRINSTALLDIR/infernal/binaries"
export VADREASELDIR="$VADRINSTALLDIR/infernal/binaries"
export VADRBIOEASELDIR="$VADRINSTALLDIR/Bio-Easel"
export VADRSEQUIPDIR="$VADRINSTALLDIR/sequip"
export VADRBLASTDIR="$VADRINSTALLDIR/ncbi-blast/bin"
export PERL5LIB="$VADRSCRIPTSDIR":"$VADRSEQUIPDIR":"$VADRBIOEASELDIR/blib/lib":"$VADRBIOEASELDIR/blib/arch":"$PERL5LIB"
export PATH="$VADRSCRIPTSDIR":"$PATH"

After adding the export lines to your .bashrc or .zshrc file, source that file
to update your current environment with the command:

source ~/.bashrc

OR

source ~/.zshrc

---
If you are using the C shell, add the following
lines to the end of your '.cshrc' file in your home
directory:

setenv VADRINSTALLDIR <full path to directory in which you ran vadr-install.sh>
setenv VADRSCRIPTSDIR "$VADRINSTALLDIR/vadr"
setenv VADRMODELDIR "$VADRINSTALLDIR/vadr-models"
setenv VADRINFERNALDIR "$VADRINSTALLDIR/infernal/binaries"
setenv VADREASELDIR "$VADRINSTALLDIR/infernal/binaries"
setenv VADRBIOEASELDIR "$VADRINSTALLDIR/Bio-Easel"
setenv VADRSEQUIPDIR "$VADRINSTALLDIR/sequip"
setenv VADRBLASTDIR "$VADRINSTALLDIR/ncbi-blast/bin"
setenv PERL5LIB "$VADRSCRIPTSDIR":"$VADRSEQUIPDIR":"$VADRBIOEASELDIR/blib/lib":"$VADRBIOEASELDIR/blib/arch":"$PERL5LIB"
setenv PATH "$VADRSCRIPTSDIR":"$PATH"

After adding the setenv lines to your .cshrc file, source that file
to update your current environment with the command:

source ~/.cshrc

(To determine which shell you use, type: 'echo $SHELL')

---
If you are using the C shell, add the following
lines to the end of your '.cshrc' file in your home
directory:

setenv VADRINSTALLDIR <full path to directory in which you ran vadr-install.sh>
setenv VADRSCRIPTSDIR "$VADRINSTALLDIR/vadr"
setenv VADRMODELDIR "$VADRINSTALLDIR/vadr-models"
setenv VADRINFERNALDIR "$VADRINSTALLDIR/infernal-dev/src"
setenv VADREASELDIR "$VADRINSTALLDIR/infernal-dev/easel/miniapps"
setenv VADRBIOEASELDIR "$VADRINSTALLDIR/Bio-Easel"
setenv VADRSEQUIPDIR "$VADRINSTALLDIR/sequip"
setenv VADRBLASTDIR "$VADRINSTALLDIR/ncbi-blast/bin"
setenv PERL5LIB "$VADRSCRIPTSDIR":"$VADRSEQUIPDIR":"$VADRBIOEASELDIR/blib/lib":"$VADRBIOEASELDIR/blib/arch":"$PERL5LIB"
setenv PATH "$VADRSCRIPTSDIR":"$PATH"

After adding the setenv lines to your .cshrc file, source that file
to update your current environment with the command:

source ~/.cshrc

(To determine which shell you use, type: 'echo $SHELL')

```
---

### If you get an error about `PERL5LIB` being undefined...

If you use bash or zsh, change the PERL5LIB line in your `~/.bashrc` or
`~/.zshrc` file to:

```
export PERL5LIB="$VADRSCRIPTSDIR":"$VADRSEQUIPDIR":"$VADRBIOEASELDIR/blib/lib":"$VADRBIOEASELDIR/blib/arch"
````

or if you use C shell, change the PERL5LIB line in your `~/.cshrc`
file to:

```
setenv PERL5LIB "$VADRSCRIPTSDIR":"$VADRSEQUIPDIR":"$VADRBIOEASELDIR/blib/lib":"$VADRBIOEASELDIR/blib/arch"
```

And then execute `source ~/.bashrc`, `source ~/.zshrc`, or `source ~/.cshrc` again.

---
## Verifying successful installation with test runs<a name="tests"></a>

The VADR package includes some tests you can run to make sure that
your installation was successful and that your environment variables
are set-up correctly.

There are two shell scripts for running tests; with respect to the
installation directory they are:

1. `vadr/testfiles/do-install-tests-local.sh`
2. `vadr/testfiles/do-install-tests-parallel.sh`

The VADR `v-annotate.pl` script can be run locally on your computer or
in [parallel](annotate.md#exampleparallel) on a compute farm. These
two test files test each of those modes.  If you plan to run the
scripts locally at least some of the time, then run
`do-install-tests-local.sh`. If you plan to run the scripts on a
compute farm at least some of the time, then run
`do-install-tests-parallel.sh`.

You can run the scripts like this:

```
$VADRSCRIPTSDIR/testfiles/do-install-tests-local.sh
```
and 
```
$VADRSCRIPTSDIR/testfiles/do-install-tests-parallel.sh
```

These scripts can take up to several minutes to run. 
If something goes wrong, the `local` script will exit quickly. If the 
compute farm is busy, the `parallel` script make take longer as the
relevant jobs wait to run.

If one or both of the scripts fail immediately with a warning like:

`Can't locate LWP/Simple.pm in @INC (you may need to install the
LWP::Simple module)`

Or something similar but with `Inline` instead of `LWP`, then you will
need to install the perl `LWP` and/or `Inline` modules as described
[here.](#inline)

Below is an example of the expected output for
`do-install-tests-local.sh`:

```
# v-test.pl :: test VADR scripts [TEST SCRIPT]
# VADR 1.0 (Nov 2019)
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# date:    Thu Nov 21 14:24:20 2019
#
# test file:                    /usr/local/vadr-install-dir/vadr/testfiles/noro.r10.local.testin
# output directory:             n10-local
# forcing directory overwrite:  yes [-f]
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# Parsing test file                                  ... done. [    0.0 seconds]
# Running command  1 [annotate-noro-10-local]        ... done. [   45.2 seconds]
#	checking va-noro.r10/va-noro.r10.vadr.pass.tbl                                                                ... pass
#	checking va-noro.r10/va-noro.r10.vadr.fail.tbl                                                                ... pass
#	checking va-noro.r10/va-noro.r10.vadr.sqa                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.sqc                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.ftr                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.sgm                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.mdl                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.alt                                                                     ... pass
#	checking va-noro.r10/va-noro.r10.vadr.alc                                                                     ... pass
#	removing directory va-noro.r10                               ... done
#
#
# PASS: all 9 files were created correctly.
#
#
# Output printed to screen saved in:                   n10-local.vadr.log
# List of executed commands saved in:                  n10-local.vadr.cmd
# List and description of all output files saved in:   n10-local.vadr.list
#
# All output files created in directory ./n10-local/
#
# Elapsed time:  00:00:45.73
#                hh:mm:ss
# 
[ok]
# v-test.pl :: test VADR scripts [TEST SCRIPT]
# VADR 1.0 (Nov 2019)
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# date:    Thu Nov 21 14:24:29 2019
#
# test file:                    /usr/local/vadr-install-dir/vadr/testfiles/dengue.r5.local.testin
# output directory:             d5-local
# forcing directory overwrite:  yes [-f]
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# Parsing test file                                  ... done. [    0.0 seconds]
# Running command  1 [annotate-dengue-5-local]       ... done. [   44.2 seconds]
#	checking va-dengue.r5/va-dengue.r5.vadr.pass.tbl                                                              ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.fail.tbl                                                              ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.sqa                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.sqc                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.ftr                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.sgm                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.mdl                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.alt                                                                   ... pass
#	checking va-dengue.r5/va-dengue.r5.vadr.alc                                                                   ... pass
#	removing directory va-dengue.r5                              ... done
#
#
# PASS: all 9 files were created correctly.
#
#
# Output printed to screen saved in:                   d5-local.vadr.log
# List of executed commands saved in:                  d5-local.vadr.cmd
# List and description of all output files saved in:   d5-local.vadr.list
#
# All output files created in directory ./d5-local/
#
# Elapsed time:  00:00:44.97
#                hh:mm:ss
# 
[ok]
```

The two most important lines are the lines that begins with `# PASS`

```
PASS: all 9 files were created correctly.
PASS: all 9 files were created correctly.
```

This means that the test has passed. You should see similar 
lines when you run the other tests. If you do not and need help
figuring out why, email me at eric.nawrocki@nih.gov.

---
## Further information

* [`v-annotate.pl` example usage and command-line options](annotate.md#top)
* [`v-build.pl` example usage and command-line options](build.md#top)
* [VADR output formats](formats.md#top)

---
#### Questions, comments or feature requests? Send a mail to eric.nawrocki@nih.gov.


