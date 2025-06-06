## Process this file with autoconf to produce the configure script

## Copyright (C) 2016 Divvun/Giellatekno/UiT

## This program is free software: you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation, either version 3 of the License, or
## (at your option) any later version.

## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.

## You should have received a copy of the GNU General Public License
## along with this program.  If not, see <http://www.gnu.org/licenses/>.

# The following things just need to be at the top of all configure.ac files:

# AC_INIT sets up the project metadata:
# first field is the name of the "software"
# second field is the version identifier - iso 8901 date is good if you
#   have no other versioining scheme in mind
# third field is email address for bug reports
# fourth field is the name of the package made by make dist, excluding .tar.gz
# fifth field is the project web address
AC_INIT([giellaltkeyboards-waw], [20130628], [feedback@divvun.no],
        [giellaltkeyboards-waw], [http://divvun.no])
# AC_REVISION is used to get SVN revision into bug reports
AC_REVISION([$Revision$])
# These configuration dirs hide some extra cruft
AC_CONFIG_AUX_DIR([build-aux])

# AM_INIT_AUTOMAKE sets up make conventions
AM_INIT_AUTOMAKE([1.11 -Wall -Werror foreign -Wno-portability])
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

# The following Giella specific variables are used to make external software
# work; HFST analysers, spell-checkers and so on. These also control
# some temporary file names etc.

# GTLANG is the language code used to identify this project; it should be same
# as the directory name in gtsvn and same as ISO 639 three-letter code for the
# language if possible
AC_SUBST([GTLANG], [waw])

# GTLANG2 is the shortest unambiguous language code for this project; it
# should be the ISO 639-1 two-letter code if possible, otherwise usually same
# as above
AC_SUBST([GTLANG2], [waw])

# This is the main motor of the keyboard generation, it needs to be available.
AC_PATH_PROG([KBDGEN], [kbdgen], [no], [$PATH$PATH_SEPARATOR$with_kbdgen])
AS_IF([test x$KBDGEN = xno ],
      [AC_MSG_ERROR([You need kbdgen to build the keyboards. See https://github.com/divvun/kbdgen])
])

# `convert` is needed for icon generation, it must be available.
AC_PATH_PROG([CONVERT], [convert], [no], [$PATH$PATH_SEPARATOR$with_convert])
AS_IF([test x$CONVERT = xno ],
      [AC_MSG_ERROR([The ImageMagic command 'convert' is needed for icon generation. Please install ImageMagic using your preferred package manager.])
])

# List all non-script files processed by Autoconf.
AC_CONFIG_FILES([Makefile])

# This must be near the end of all configure.ac files:
AC_OUTPUT

# Prints the informative blurb at the end of the ./configure command
cat<<EOF
-- Building $PACKAGE_STRING:

For more ./configure options, run ./configure --help

To build installation packages for the desktop keyboards, do:
    make
EOF
