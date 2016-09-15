Sublime for Go (golang), setup properly
=======================================

| This setup assumes `C:\GoPath` as your GOPATH.  Changes any
| occurrences of this string into your GOPATH if you chose otherwise.

Setup environment variables:

 * Hit `Windows+S`, type in `environment variables` and start `Edit the system environment variables`.

 * In the `Advanced` tab, click the `Environment variables` (lower part of the window).

 * Under `System variables`:

   * set `GOPATH` to value `C:\GoPath`.
   * modify `Path` and append the value `;C:\GoPath\bin` (separate the previous path with the `;`)
   * set `GOROOT` to value `C:\Go`.

 * If you're going to use `Git Bash`, dump this in your `~/.profile` (both Mac OS X and Windows should work with that):

```
export GOPATH=/c/GoPath
export PATH=/c/GoPath/bin:$PATH
```

Install [Sublime Text 3](https://www.sublimetext.com/3).

Make sure you have [Package Control](https://packagecontrol.io/installation) installed.

Install Sublime plugins:

* Hit `Control+Shift+P` (opens the Palette) and type in: `install pack`.. you should see
  `Package Control: Install Package` in the list. If you don't see
  that, install `Package Control` above.

* If `Package Control: Install Package` is shown, hit `<Enter>` to pop the next box.


* Punch in `GoSublime` and hit enter.  It will install [GoSublime](https://github.com/DisposaBoy/GoSublime)

* Hit `Control+Shift+P`, type in `package install`, hit `<Enter>` and
  type in `GoGuru`. Hit `<Enter>` again to install [GoGuru](https://github.com/alvarolm/GoGuru).

* Hit `Control+Shift+P`, type in `package install`, hit `<Enter>` and
  type in `Godef`. Hit `<Enter>` again to install [Godef](https://github.com/buaazp/Godef).

* Hit `Control+Shift+P`, type in `package install`, hit `<Enter>` and
  type in `SublimeLinter`. Hit `<Enter>` again to install [SublimeLinter 3](http://sublimelinter.readthedocs.io/en/latest/installation.html).

* Hit `Control+Shift+P`, type in `package install`, hit `<Enter>` and
  type in `SublimeLinter golint`. Hit `<Enter>` again to install [SublimeLinter-contrib-golint](https://github.com/sirreal/SublimeLinter-contrib-golint).

* Hit `Control+Shift+P`, type in `package install`, hit `<Enter>` and
  type in `SublimeLinter gotype`. Hit `<Enter>` again to install [https://github.com/sirreal/SublimeLinter-contrib-gotype).

Install some go command line tools:

* On the command line, run:

```
go get -u -v github.com/rogpeppe/godef
go get -u -v golang.org/x/tools/cmd/guru
go get -v golang.org/x/tools/cmd/goimports
go get -u -v github.com/golang/lint/golint
go get -u -v golang.org/x/tools/cmd/gotype
```

(GoCode is integrated into GoSublime.. won't use an external version)

Configuring Sublime Text 3's plugins:

* Open menu `Preferences` -> `Package Settings` -> `GoSublime` -> `Settings - User` and drop this in there:

```
{
    "fmt_cmd": ["goimports"]
}
```

* Default bindings for GoGuru:

```
[{ "keys": ["ctrl+shift+g"], "command": "go_guru"}]
```

* Default _Go to definition_ with _GoSublime_:

```
["keys": ["ctrl+.", "ctrl+g"], "command": "gs_doc",...}]
```

* `golint` and `gotype` are enabled automatically, check the Palette
  under `SublimeLinter` for more options.  One notable function is
  `SublimeLinter: Show all errors`.. discover the keyboard shortcut in
  the Palette and memorize it.


Restart Sublime Text 3
----------------------

If you have any issues, please open an issue on this repo.. I want
that recipe to be flawless to onboard new Go developers on Sublime.