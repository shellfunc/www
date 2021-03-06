## http://www.shellfunc.com/


## Web shell

A web shell is a shell-esque interface that enables a web server to be remotely accessed.

A web shell is unique in that a web browser is used to interact with it.

A web shell could be programmed in any programming language that is supported on a server. Web shells are most commonly written in the PHP programming language due to the widespread usage of PHP for web applications. However, Active Server Pages, ASP.NET, Python, Perl, Ruby, and Unix shell scripts are also used, although these languages are less commonly used

Using network monitoring tools, an attacker can find vulnerabilities that can potentially allow delivery of a web shell. These vulnerabilities are often present in applications that are run on a web serve

An attacker can use a web shell to issue shell commands, perform privilege escalation on the web server, and the ability to upload, delete, download, and execute files to and from the web server

## The shell Function
The shell function is unlike any other function other than the wildcard function (see The Function wildcard) in that it communicates with the world outside of make.

The shell function performs the same function that backquotes ' perform in most shells: it does command expansion. 


This means that it takes as an argument a shell command and evaluates to the output of the command. The only processing make does on the result is to convert each newline (or carriage-return / newline pair) to a single space.

If there is a trailing (carriage-return and) newline it will simply be removed.

The commands run by calls to the shell function are run when the function calls are expanded (see How make Reads a Makefile). Because this function involves spawning a new shell, you should carefully consider the performance implications of using the shell function within recursively expanded variables vs. simply expanded variables (see The Two Flavors of Variables).

After the shell function or ‘!=’ assignment operator is used, its exit status is placed in the .SHELLSTATUS variable.

Here are some examples of the use of the shell function:

    contents := $(shell cat foo)

sets contents to the contents of the file foo, with a space (rather than a newline) separating each line.

    files := $(shell echo *.c)

sets files to the expansion of ‘*.c’. Unless make is using a very strange shell, this has the same result as ‘$(wildcard *.c)’ (as long as at least one ‘.c’ file exists).
