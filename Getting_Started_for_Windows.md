Getting Started with Golang - Windows
=====================================

Install Go
----------

Download Go from:

* http://golang.org/dl/

and download and install the .MSI package WITH ALL DEFAULT. Just hit
NEXT.

> * If a previous version was already installed, go to "Add / Remove
>   Programs", and remove it beforehand.

Create your GOPATH
------------------
The GOPATH is where all your Go code will live.

Create new folder in C:\ named "GoPath"

Go to the `System` control panel, click the `Advanced` tab. Select
`Environment Variables` and under `System variables`:

 * add GOPATH variable, set it to "C:\GoPath"


Install Git
-----------

Download from:

* http://git-scm.com/downloads


Install go tools
----------------

Open a NEW Command Prompt (`cmd.exe` with new env vars), paste this in to install
those sweet tools:

    go get -u -ldflags -H=windowsgui github.com/nsf/gocode/...
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
 
   * Hit `Enter` to accept `Install extensions`

   * From the list, select `Go`, and click `Install`. Wait and then click `Enable`.
   
   
Setup `Go` environment variables
--------------------------------

In VS Code, open `%USERPROFILE%/.profile`.

Tweak it and add these:

    export GOPATH=/c/GoPath
    export PATH=/c/GoPath/bin:$PATH
    # Uncomment to load your SSH keys when you open Git Bash
    # eval $(ssh-agent)
    # ssh-add $HOME/.ssh/id_rsa


Setup of global `Git` configuration
-----------------------------------

Open the file `%USERPROFILE%/.gitconfig` in VS Code.

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

Open "Git Gui" (right click on the Desktop, or run `git gui` in Git
bash)

Select `Clone Existing Repository`, punch in:

* Source location: `git@github.com:abourget/getting-started-with-golang`
* Target directory: `C:\GoPath\src\github.com\abourget\getting-started-with-golang`

Go to Atom, select "File" -> "Add Project Folder", and navigate to
`C:\GoPath\src\github.com\abourget\getting-started-with-golang`.

In `Git Bash`, run:

    cd /c/GoPath/src/github.com/abourget/getting-started-with-golang
    go install -v
    getting-started-with-golang

Modify `main.go` in this repository and rerun `go install -v` to compile and
`getting-started-with-golang` to re-execute the program.
