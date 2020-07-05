# Create a NumPy build environment for docs

These instructions assume:

* Anaconda is installed
* You have a local clone of numpy
* You're in its top level

```sh
# Create a fresh environment with python 3.8.
# Ignore the "ncurses" message.
conda create --name doc-build-38 python==3.8

# Switch to the new environment
conda activate doc-build-38

# Install Cython
conda install Cython

# Build/install NumPy
2>&1 pip install . | tee pip_install.log

# Install additional requirements for the docs
2>&1 pip install -r doc_requirements.txt | tee pip_install_doc_req.log

# Install additional sphinx dependencies that are included as submodules
cd doc
git submodule update --init

# You're now ready to build the docs. 
# To preview your changes after you've edited the .rst, you'll rerun this step.
2>&1 make html | tee make_html.log
```
Thanks to [@rossbar](github.com/rossbar/) for providing and commenting this.

The `tee` commands are optional (for instance, you can just run `pip install -r doc_requirements.txt`), but it's helpful to have a log -- particularly for the HTML build.

## HTML build success
You'll see
```
build succeeded.

The HTML pages are in build/html.
python3.8 postprocess.py html build/html/*.html

Build finished. The HTML pages are in build/html.
```
Be alert to "successes" where nothing got built (perhaps you forgot to save your changes):
```
Build finished. The HTML pages are in build/html.
no targets are out of date.
```

## HTML build failures

### Failures from bad .rst coding

A failed `make html` looks like:
```
build finished with problems, 10 warnings.
Makefile:179: recipe for target 'html-build' failed
make: *** [html-build] Error 1
```
Grep the log for `WARNING`; for example:
```
/home/bjn/numpy_git/numpy-1/doc/source/dev/gitwash/development_setup.rst:106: WARNING: Bullet list ends without a blank line; unexpected unindent.
```

### 'version check' failed

`make html` may fail immediately with:

```
$ make html
installed numpy e84f49e62d != current repo git version '5345c2575a'
use "make dist" or "GITVER=e84f49e62d make html ..."
Makefile:93: recipe for target 'version-check' failed
make: *** [version-check] Error 1
```
The scrupulous fix is to go up a level (that is, from doc to numpy) and rebuild numpy by rerunning  `pip install -e `. This is time-consuming because in addition to pip's running time, `make html` will rebuild everything. The quick workaround is to set `GITVER` as indicated, but you'll want to do the real update before committing.

## Previewing the revised page

To view the HTML in your browser, the equivalent of the docs top level -- that is, of 

```
https://numpy.org/doc/stable
```
 or 

```
https://numpy.org/devdocs
```

is

```
file://path-to-your-numpy/doc/build/html
```

So for instance your revision of 
```
https://numpy.org/doc/stable/user/whatisnumpy.html
```
will be at 
```
file://path-to-your-numpy/doc/build/html/user/whatisnumpy.html
```

