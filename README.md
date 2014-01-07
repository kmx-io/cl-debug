
CL-DEBUG
========

A cross-package debug facility for Common Lisp.

This is a tiny but powerful package that provides a unified way to enable or
disable debug-specific code. Debugging code can be enabled or disabled relative
to program features denoted by either a symbol or a keyword. 

This approach is to be contrasted with the notion of log levels which can lack
in granularity, often giving too few information or too much. Selecting debug
code by features improves the debugging experience and greatly speeds up the
identification of many bugs.

The interface is very similar to that of __\*FEATURES\*__ with the difference
that it is not a reader macro.
Source code is only 23 lines of code,
the only exported symbol is __DEBUG-P__ and
using it is pretty straightforward.

Usage
-----

For instance consider this source code taken from the database handling code
of a popular data driven website :

    (when (debug-p :database)
      ;; Log some database infos
      ...)

And in the model handling code :

    (when (debug-p (or :database :model))
            ;;  Log some model info
            ...)

Then in your REPL or by creating some user interface knob, your developers
or users can activate this specific debugging code, without invoking
a logging hell across all your programs :

    (setf (debug-p :database) t)

So if your code is spanned across multiple packages - for instance in this example
database and model are not in the same package - you can still enable or disable
all the debugging code related to the precise features you are currently working on.


Licensing
---------

The code is released under the ISC license meaning that it can be used
everywhere you might want to.


    CL-DEBUG
    
    Copyright 2013 LowH <code@lowh.net>
    
    Permission to use, copy, modify, and distribute this software for any
    purpose with or without fee is hereby granted, provided that the above
    copyright notice and this permission notice appear in all copies.
    
    THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
    WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
    MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
    ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
    WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
    ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
    OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
