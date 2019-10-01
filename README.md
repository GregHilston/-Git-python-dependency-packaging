# Python Dependency Packaging

This repository is a demonstration on how Python developers can distribute their applications to non-technical individuals, and still have their dependencies packaged up in an easy to use way.

## [Pyinstaller](https://www.pyinstaller.org/)

For those of you that don't know of [Pyinstaller](https://www.pyinstaller.org/)

> PyInstaller freezes (packages) Python applications into stand-alone executables, under Windows, GNU/Linux, Mac OS X, FreeBSD, Solaris and AIX.

### License

This incredibly convenient project also is distributed under the [gpl-2.0](https://tldrlegal.com/license/gnu-general-public-license-v2) [license](https://www.pyinstaller.org/license.html), which means you can use it in free and open source projects along with commercial projects.

## Our Dependencies

For this sample project, the only dependency we installed was `flask`, which came with its own dependencies. If we were to send just our `app.py` file to our clients, they would not be able to run our program without installing our dependencies, described in our `requirements.txt`.

### Installing As A Developer

Python developers have created the formality of always providing a `requirements.txt` with one's project, to explain how one can get all the dependencies. If given a `requirements.txt`, one can activate a virtual environment by running

`$ source venv/bin/activate`

and then install the dependencies by using

`$ pip3 install -r requirements`

Which will instal the dependencies **only** in the activated environment, leaving your system environment pollution free.

### Preparing For A Non-Technical Person

While the instructions above will work, those steps are often too difficult for a non-technical individual. I would never expect a client of mine to install their own dependencies, so we must have a simpler way. So we'll install pyinstaller inside our activated virtualenv, by running

`$ pip3 install pyinstaller`

Now that we have pyinstaller, we'll call it by running

`$ pyinstaller --onefile app.py -n app.exe`

This will generate a file called `app.exe` in our `dist` folder. Run that executable by running

`$ ./app.exe`

_Note: This executable can now be called without having your `venv` activated_

You can now distribute this `app.exe` to other users.

**Please note that pyinstaller does not support cross building. So an exectuable made on an OSX machine will only work on another OSX machine**

## Moving Forward

One could use Pyinstaller in their CiCd pipeline, to build an executable upon merges to a git `master` branch or on a github release, allowing an easy way to shares executables with non-technical individuals.
