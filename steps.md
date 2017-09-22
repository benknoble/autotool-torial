# Steps

1. Prepare initial files (`src`, `*.am`, `configure.ac`)

```bash
$ ls -R

LICENSE
Makefile.am
README.md
configure.ac
src

./src:
Makefile.am
main.c
```

2. `autoreconf --install`

```bash
$ autoreconf --install

configure.ac:8: installing './compile'
configure.ac:6: installing './install-sh'
configure.ac:6: installing './missing'
src/Makefile.am: installing './depcomp'

$ ls -R

LICENSE
Makefile.am
Makefile.in
README.md
aclocal.m4
autom4te.cache
compile
config.h.in
configure
configure.ac
depcomp
install-sh
missing
src

./autom4te.cache:
output.0
output.1
requests
traces.0
traces.1

./src:
Makefile.am
Makefile.in
main.c
```

3. Configure

```bash
$ ./configure

checking for a BSD-compatible install... /usr/local/bin/ginstall -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/local/bin/gmkdir -p
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands

$ ls -R

LICENSE
Makefile
Makefile.am
Makefile.in
README.md
aclocal.m4
autom4te.cache
compile
config.h
config.h.in
config.log
config.status
configure
configure.ac
depcomp
install-sh
missing
src
stamp-h1

./autom4te.cache:
output.0
output.1
requests
traces.0
traces.1

./src:
Makefile
Makefile.am
Makefile.in
main.c
```

4. Make

```bash
$ make

/Applications/Xcode.app/Contents/Developer/usr/bin/make  all-recursive
Making all in src
gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc  -g -O2   -o hello main.o
make[2]: Nothing to be done for `all-am'.

$ src/hello

Hello world!
This is amhello 1.0 .
```

5. Make distcheck

```bash
$ make distcheck

#... omitted ...
=============================================
amhello-1.0 archives ready for distribution:
amhello-1.0.tar.gz
=============================================

$ tar ztf amhello-1.0.tar.gz

amhello-1.0/
amhello-1.0/aclocal.m4
amhello-1.0/compile
amhello-1.0/config.h.in
amhello-1.0/configure
amhello-1.0/configure.ac
amhello-1.0/depcomp
amhello-1.0/install-sh
amhello-1.0/Makefile.am
amhello-1.0/Makefile.in
amhello-1.0/missing
amhello-1.0/src/
amhello-1.0/src/main.c
amhello-1.0/src/Makefile.am
amhello-1.0/src/Makefile.in
```
