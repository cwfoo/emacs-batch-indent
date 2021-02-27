# emacs-batch-indent
`emacs-batch-indent` is a command line program that uses Emacs in batch mode to
indent **Common Lisp**, **Emacs Lisp**, and **Scheme** code given on standard
input. The indented code is written to standard output. The script was
originally written for use as Vim's `equalprg` to indent Lisp.

Example:
```sh
echo '(let ((x 1)
(y 2))
(+ x y))' | emacs-batch-indent scheme
```

Result written to standard output:
```scheme
(let ((x 1)
      (y 2))
  (+ x y))
```


## Requirements
* `/bin/sh`
* GNU Emacs


## Installation
* Download the `emacs-batch-indent` script.
* Make the script executable: `chmod +x ./emacs-batch-indent`.
* At this point, you should be able to display the help message by running
  `./emacs-batch-indent --help`.


## Usage
`emacs-batch-indent` takes its input from standard input, and outputs the
indented code to standard output.

Examples:

* Common Lisp: `./emacs-batch-indent cl < myprogram.lisp`
* Emacs Lisp: `./emacs-batch-indent elisp < myprogram.el`
* Scheme: `./emacs-batch-indent scheme < myprogram.scm`

By default, `emacs-batch-indent` indents using spaces. To indent using tabs,
use the `--tabs` option. For example:
`./emacs-batch-indent cl --tabs < myprogram.lisp`.

The `--help` (or `-h`) option displays the help message.


### Usage in Vim
`emacs-batch-indent` can be used as the external program for Vim's `=` command
(`equalprg`). For example, to use `emacs-batch-indent` to indent Scheme code in
Vim when using the `=` command, add the following to your Vim configuration
file:

```vim
" Note: This assumes that emacs-batch-indent is somewhere in your $PATH.
autocmd FileType scheme setlocal equalprg=emacs-batch-indent\ scheme
```


## License
The files in this project are licensed under the GNU General Public License,
version 3 or (at your option) any later version.


## Contributing
Bug reports, suggestions, and patches should be submitted on GitHub:
https://github.com/cwfoo/emacs-batch-indent


## Development
To run the unit tests: `./test-emacs-batch-indent`.

`emacs-batch-indent` is known to work as intended on:
* GNU Emacs 26.3 on Ubuntu 20.04.1
* GNU Emacs 27.1 on FreeBSD 12.2

Project started on 2021-02-15.
