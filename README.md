# flycheck-google-cpplint.el

Add Google C++ Style checker for [Flycheck](https://github.com/flycheck/flycheck).

If you're want to write code according to the [Google C++ Style Guide](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml), this will help a great deal.

I recommend that the package [google-c-style](http://melpa.milkbox.net/#/google-c-style) also installed with.

# Usage

## Install cpplint.py

```
$ wget http://google-styleguide.googlecode.com/svn/trunk/cpplint/cpplint.py
$ sudo mv cpplint.py /usr/local/bin/cpplint.py
$ sudo chmod 755 /usr/local/bin/cpplint.py
```

You should be able to run the `cpplint.py` command.

```
$ cpplint.py
```

## Install package

Install the ELPA package from [MELPA] with `M-x package-install RET flycheck-google-cpplint`.

In your [Cask](https://cask/cask) file:

```
(source gnu)
(source melpa)

(depends-on "flycheck")
(depends-on "flycheck-google-cpplint")
```

## Add to your Emacs config

```
(require 'flycheck)
(require 'flycheck-google-cpplint)

(flycheck-add-next-checker 'c/c++-cppcheck
                           'c/c++-googlelint)

(global-flycheck-mode)
```

## Configure for cpplint.py

```
(custom-set-variables
 '(flycheck-googlelint-verbose "3")
 '(flycheck-googlelint-filter "-whitespace,+whitespace/braces")
 '(flycheck-googlelint-root "project/src")
 '(flycheck-googlelint-linelength "120")
 )
```
