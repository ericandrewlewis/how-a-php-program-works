# How a PHP program works

`program.php` is a PHP script that outputs "Hi".

To run the program, you need to have PHP installed on your computer.

On the command line, run `php program.php` to see its output.

Install PECL, the package manager for PHP extensions and libraries. [How to install Pecl on Mac OS X](http://jason.pureconcepts.net/2012/10/install-pear-pecl-mac-os-x/).

Install the PHP extension [vld](http://pecl.php.net/package/vld), via pecl by running `pecl install vld-0.13.0`.

Run `php -dextension=vld.so -dvld.active=1 -dvld.execute=0 program.php`. This shows
the series of [opcodes](http://php.net/manual/en/internals2.opcodes.php) generated from the program.

You'll get this:

```
$ php -dextension=vld.so -dvld.active=1 -dvld.execute=0 program.php
Finding entry points
Branch analysis from position: 0
Jump found. Position 1 = 1, Position 2 = 4
Branch analysis from position: 1
Jump found. Position 1 = 4
Branch analysis from position: 4
Jump found. Position 1 = -2
Branch analysis from position: 4
filename:       /Users/eric/Desktop/Projects/2015/01/how-a-php-program-works/program.php
function name:  (null)
number of ops:  5
compiled vars:  none
line     #* E I O op                           fetch          ext  return  operands
-------------------------------------------------------------------------------------
   2     0  E > > JMPZ                                                     <bool>, ->4
   3     1    >   PRINT                                            ~0      'Hi%21'
         2        FREE                                                     ~0
   4     3      > JMP                                                      ->4
         4    > > RETURN                                                   1

branch: #  0; line:     2-    2; sop:     0; eop:     0; out1:   1; out2:   4
branch: #  1; line:     3-    4; sop:     1; eop:     3; out1:   4
branch: #  4; line:     4-    4; sop:     4; eop:     4; out1:  -2
path #1: 0, 1, 4,
path #2: 0, 4,
```