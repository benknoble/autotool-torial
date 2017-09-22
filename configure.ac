# process with autoconf

# takes package name, version, email for bugs
AC_INIT([amhello], [1.0], [bug-report@address])
# takes options for *automake* (foreign states that it is not GNU compliant)
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
# search for C compiler and use CC as it's name
AC_PROG_CC
# creates a header as named gathering '#define's from other macros
AC_CONFIG_HEADERS([config.h])
# generated from *.in templates by configure
# also used to find Makefile.am files
AC_CONFIG_FILES([
                 Makefile
                 src/Makefile
                 ])
# produce the script
AC_OUTPUT
