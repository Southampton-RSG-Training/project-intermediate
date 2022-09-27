# Setup for Lesson
## Open a Terminal ##

For this lesson, first you need to be able to open a terminal:

- **On Windows:** run "Git Bash", to install git bash go here [https://gitforwindows.org/](https://gitforwindows.org/) click download and select 'Git-X.XX.X-64-bit.exe' from the assets list.
- **On Mac OS X:** accessed by opening the “Terminal” application, which can be found in the “Utilities” folder which is in your “Applications” folder.
- **On Linux:** this will depend on the Linux distribution you are running, but you should be able to find a "Terminal" application in your desktop's application menu.


## Git Setup ##

### Windows
We'll be using Git Bash for both git and a shell to run it in. If you've already installed Git Bash then go to the next section. Otherwise, go to [git for windows](https://gitforwindows.org/) and click **Download**, then install it. 
Most of the options can be left on default, but be sure you check these:

- **Choosing the default editor used by Git:** Make sure **Nano** is selected from the drop-down. If you're comfortable with other editors, feel free to change it, but we recommend Nano - we use it as it's present on Windows, Mac *and* Linux. If you change it, you might not quite match what we're doing on-screen.
- **Adjusting your PATH environment:** Make sure **Git from the command line and also from 3rd-party software** is selected.
- **Choosing HTTPS transport backend:** Make sure **Use the native Windows Secure Channel Library** is selected.
- **Configuring the terminal emulator to use with Git Bash:** Make sure **Use Windows' default console window** is selected.

#### Mac OS
To use Git you must install the Apple Command Line Tools, this may take a few minutes.  

You can obtain these [from Apple](https://developer.apple.com/download/more/?name=command%20line%20tools%20for%20xcode%2012) (requires your Apple ID)

- Select **Command Line Tools for Xcode 12** and click the link to download the dmg archive.
- If prompted, choose to allow downloads from developer.apple.com
- Open the downloaded dmg archive from the Downloads folder
- Double-click the Command Line Tools.pkg icon to install

Alternatively, you can install the tools from the command line:

~~~
$ xcode-select --install
~~~
{: .language-bash}

#### Linux
Git comes pre-installed on most Linux distributions. You can test if it's installed by running `git --version`. 
If it's not installed, you can install it by running `sudo apt-get install git` or `sudo yum install git`, depending on 
your distribution.

## GitHub ##
Later on in the session, we'll be demonstrating how to share work with collaborators using [GitHub](https://github.com/). You'll need to [create an account there](https://github.com/signup). As your GitHub username will appear in the URLs of your projects there, it's best to use a short, clear version of your name if you can.

In addition, we'll need to set up SSH access to GitHub from your computer. This is how GitHub checks your identity when you try to access it - and is more secure than a password. To set up SSH access, we generate a pair of keys - one public, one private. We want to add the public key to GitHub, whilst the private one stays on our computer.

There are full guides in the GitHub documentation for how to [Make an SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [Add an SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). However today we have simplified it like so:

If you already have an ssh key you can use it for Github by coping the public key into the clipboard and pasting it into the GitHub settings page.

First we need to create a variable to store your GitHub email. Copy this command, substituting the email you signed up to GitHub with for `your_github_email@example.com`:
~~~
$ my_gh_email=your_github_email@example.com
~~~
{: .language-bash}

Then we can run the following command to generate a key-pair and display the public half:
~~~
$ ssh-keygen -t ed25519 -C $my_gh_email; eval "$(ssh-agent -s)"; ssh-add ~/.ssh/id_ed25519; cat ~/.ssh/id_ed25519.pub
~~~
{: .language-bash}

You will need to press enter a few times to select default options, and set the passphrase to empty.

Copy the last line of output that starts with `ssh-ed25519` and ends with your email (it may have gone over multiple lines if your terminal isn't wide enough).

![SSH-Output](fig/setup-SSH-Output.png){:width="50%"}

Finally, go to [your Settings -> SSH keys page and add a new SSH key](https://github.com/settings/ssh/new) (you'll need to be logged into GitHub with the account you have created). Give the key a memorable name (e.g. the name of the computer you are working on) and paste the key from your clipboard into the box labelled key. Then, click **Add SSH key** and you're done!
## Python Setup ##

We recommend using the [standard Python distribution version 3.8](https://www.python.org/downloads/) using `venv` 
for virtual environments and `pip` for package management.

To download a Python distribution for your operating system,
please head to [Python.org](https://www.python.org/downloads/).
>## Recommended Python Version
> We recommend using at least Python version 3.8+ but any [supported version](https://devguide.python.org/#status-of-python-branches) should work (i.e. 3.7 onward.
> Specifically, we recommend upgrading from Python 2.7 wherever possible. Continuing to use it will likely result in difficulty finding supported dependencies or syntax errors.
{: .callout}

You can
test your Python installation from the command line with:
~~~
$ python3 --version
~~~
{: .language-bash}
If all is well with your installation, you should see something like:
~~~       
Python 3.8.2
~~~
{: .output}

To make sure you are using the standard Python distribution and not some other distribution you may have on your system,
type the following in your shell:
 ~~~
 $ python3
 ~~~
{: .language-bash}
This should enter you into a Python console and you should see something like:
 ~~~
Python 3.8.2 (default, Jun  8 2021, 11:59:35) 
[Clang 12.0.5 (clang-1205.0.22.11)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
 ~~~
{: .language-bash}
Press `CONTROL-D` or type `exit()` to exit the Python console.

### `venv` and `pip`
If you are using a Python 3 distribution from [Python.org](https://www.python.org/),
`venv` and `pip` will be automatically installed for you. If not, please make sure you have these
two tools (that correspond to your Python distribution) installed on your machine.
## PyCharm IDE
We use JetBrains's [PyCharm Python Integrated Development Environment](https://www.jetbrains.com/pycharm) for the course.
PyCharm can be downloaded from [the JetBrains website](https://www.jetbrains.com/pycharm/download).
The Community edition is fine, though if you are developing software for the purpose of academic research you may
be eligible for a free license for the Professional edition which contains extra features.