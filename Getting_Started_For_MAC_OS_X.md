Getting Started with Golang - Mac OS X
======================================

Install Go
----------

Download Go from:

* http://golang.org/dl/

and download and install the .PKG package. Uninstall any previous
install.

> If a previous version was already installed, run:
> 
>     sudo rm -rf /usr/local/go

The GOPATH is where all your Go code will live.

Run:

    mkdir ~/go


Install Git
-----------

Download from:

* http://git-scm.com/downloads



Install go tools
----------------

Open a NEW Terminal (with new env vars), paste this in to install
those sweet tools:

    # if in zsh, do also: export PATH=/usr/local/go/bin:$PATH
    export GOPATH=$HOME/go
    go get -u github.com/nsf/gocode/...
    go get -u github.com/rogpeppe/godef/...
    go get -u golang.org/x/tools/cmd/...

You might see an error with `godoc`. Ignore it.


Install VisualStudio Code
-------------------------

VisualStudio Code has one of the best support for coding in Go. It has excellent plugins and
works across platforms.

Download from:

* https://code.visualstudio.com/

After installation, do:

 * Hit <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> and type in `Install exte`
 
   * Hit `Enter` to accept `Install extentions`

   * From the list, select `Go`, and click `Install`. Wait and then click `Enable`.


Setup `Go` environment variables
--------------------------------

In VS Code, open `~/.profile`.

> If you use `zsh`, open `~/.zshrc` instead.

Tweak your profile file to add these lines and *save* the file:

    export GOPATH=$HOME/go
    export PATH=$HOME/go/bin:$PATH


Setup of global `Git` configuration
-----------------------------------

Open the file `~/.gitconfig` in VS Code.

Make sure similar lines are in there:

    [user]
	name = Your Name
	email = yourmail@example.com

Save & exit.


Setup GitHub authentication
---------------------------


### Generate a new key

Run:

    cat $HOME/.ssh/id_rsa.pub

If you see `No such file or directory`, continue on, otherwise skip
this `ssh-keygen` step and go to `Register your key on GitHub`.

Still in "Git Bash", run:

    ssh-keygen

Accept the default file name (hit ENTER).  This key gives access to
all your github repos. Secure it with a password when asked.

  * This password never leaves your computer, the key shouldn't
    either, but if lost, it is encrypted with this password.


### Register your key on GitHub

Run:

    cat $HOME/.ssh/id_rsa.pub

Go to:

* https://github.com/settings/ssh

Click "Add SSH key" (at the top right of the box).

Copy the `ssh-rsa .......` in the `Key` input field. Don't fill in
`Title` (it will use the key comment).

GitHub will ask you to confirm with your GitHub password.


Check out your first project, get ready to run and build
--------------------------------------------------------

In a terminal, run:

    mkdir -p $GOPATH/src/github.com/abourget
    cd $GOPATH/src/github.com/abourget
    git clone git@github.com:abourget/getting-started-with-golang

    cd getting-started-with-golang

    go install -v
    getting-started-with-golang

Modify `main.go` in this repository and rerun `go install -v` to compile and
`getting-started-with-golang` to re-execute the program.
