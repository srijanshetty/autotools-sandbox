# Autotools Introduction

- This is a bare bones repository which illustrates how to use autotools.
- We'll demonstrate the use of autoconf, aclocal and automake.

## autoconf

- *autoconf* is used to create **configure** files from a *configure.ac* template.
- In this example, we use **AC_PROG_CC** to ascertain the C compiler and instruct that we will *automake* will be used to generate **Makefiles**.

## aclocal

- *aclocal* reads an autoconf file and collects all the macros that will be needed when we run *autoconf*.
- *autoconf* only has a base set of macros, *aclocal* provides macros for *automake* and other custom libraries.
- After creating *configure.ac*, use run the following set of commands to generate files.

        $ aclocal
        $ autoconf

## automake

- *automake* generates a *Makefile.in* file from a *Makefile.am* template.
- The beauty of *Makefile.am* is that you only specify the target file and the source file, the rest of the details are plugged in by the tool.
- *automake* compiles the *Makefile.am* file to a *Makefile.in* file which is very close to being a *Makefile* but lacks infromaiton which is plugged in by *configure* like the name of the compiler.

        $ automake --add-missing --foreign

- **add-missing** generates additional missing files like **install-sh**. **foreign** instructs _automake_ that we are not following *GNU* standard.

## autoreconf

- When using tools from the *autotools* suite, we have to make sure that the tools are run in the correct order, which become kind of a pain when we start using additional tools like autolib. This pain is mitigated by *autoreconf* which executes all these tools in the right order.

        $ autoreconf --install --verbose



