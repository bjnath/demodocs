.. _installing-scikit-image:

Installing scikit-image
==============================================================================

How you install ``scikit-image`` depends on your needs and skill:

- Simplest solution:
  `a scientific Python distribution <#scientific-python-distributions>`_.\

- If you can install Python packages and work in virtual environments:

  - `pip <#install-via-pip>`_

  - `conda <#install-via-conda>`_

- Easy but has pitfalls: `system package manager (yum, apt-get,...) <#system-package-manager>`_

- `You're looking to contribute to scikit-image <???>`_

Supported platforms
------------------------------------------------------------------------------

- Windows 64-bit on x86 processors
- Mac OS X on x86 processors
- Linux 64-bit on x86 processors

For information on other platforms, see `Other platforms <#other-platforms>`_.

Version check
------------------------------------------------------------------------------

To see whether ``scikit-image`` is already installed or to check if an install has
worked, run the following in a Python shell or Jupyter notebook:

.. code-block:: python

  import skimage
  print(skimage.__version__)

or, from the command line

.. code-block:: bash

   python -c "import skimage; print(skimage.__version__)"

You'll see the version number if ``scikit-image`` is installed and  
a failure message otherwise.

Scientific Python distributions
------------------------------------------------------------------------------

In a single install you'll get Python, ``scikit-image`` and libraries
it depends on, and other useful scientific packages. They install into
an isolated environment, so they won't conflict with any existing
installed programs.

Drawbacks are that the install can be large and you may not get
the most recent ``scikit-image``.

We recommend one of these distributions:

- `Anaconda <https://www.anaconda.com/distribution/>`_
- `Python(x,y) <https://python-xy.github.io/>`_
- `WinPython <https://winpython.github.io/>`_

To be sure you reference your installed version in the ``scikit-image``
documentation, run the `version check <#version-check>`_ above.


Installation via pip and conda
------------------------------------------------------------------------------

These install only ``scikit-image`` and its dependencies; pip has an option to
include related packages.

.. _install-via-pip:

pip
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Prerequisites: You can use your system's command line to
install packages and are using a
`virtual environment <https://docs.python.org/3/tutorial/venv.html>`_

There's nothing to stop you from using pip without virtual environments,
but `it's a bad idea that will bite you later <???>`_. 
In particular, if you use ``pip`` without a 
virtual environment, do not use ``sudo`` or install as root.

To install the current ``scikit-image`` you'll need at least Python 3.6. If your Python
is older, you can find a compatible version of ``scikit-image`` from
`an older release <https://github.com/scikit-image/scikit-image/releases>`_.

??? Explain how to install an older ``scikit-image``

.. code-block:: sh

  # Update pip to a more recent version
  python -m pip install -U pip
  # Install scikit-image
  python -m pip install -U scikit-image

To install related packages often included
in scientific python distributions use
the command:

.. code-block:: sh

    python -m pip install scikit-image[optional]

??? why no -U?



.. _install-via-conda:

conda
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Miniconda is a bare-essentials version of the Anaconda package; you'll need to
install packages like ``scikit-image`` yourself. Like Anaconda, it installs
Python and provides virtual environments.

- `conda documentation <https://docs.conda.io>`_
- `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`_
- `conda-forge <https://conda-forge.org>`_ a channel maintained with the latest ``scikit-image`` package.


System package manager
------------------------------------------------------------------------------

Using a package manager (``yum``, ``apt-get``, etc.) to install ``scikit-learn``
or other Python packages is not your best option:

- you're likely to get an older version

- as you make updates and add new packages you can fall victim to
  dependency conflicts, just as when using pip without a virtual environment.


Additional help
------------------------------------------------------------------------------

If you still have questions, reach out via

- our `forum on image.sc <https://forum.image.sc/tags/scikit-image>`_
- our `mailing list <https://mail.python.org/mailman3/lists/scikit-image.python.org/>`_
- our `chat channel <https://skimage.zulipchat.com/>`_
- `Stack Overflow <https://stackoverflow.com/questions/tagged/scikit-image>`_


To suggest a change in the install instructions, 
`open an issue on GitHub <https://github.com/scikit-image/scikit-image/issues>`_.

Other platforms
------------------------------------------------------------------------------

We still support Windows 32-bit on x86 processors but urge switching
to Windows 64-bit.

Unsupported platforms include:

1. Linux on 32-bit x86 processors.
2. Linux on 32-bit on ARM processors (Raspberry Pi running Rapsbian):

   - While we do not officially support this distribution, we point users to
     `piwheels <https://wwww.piwheels.org>`_
     and their
     `scikit-image's specific page <https://www.piwheels.org/project/scikit-image/>`_.

   - You may need to install additional system dependencies listed for
     `imagecodecs <https://www.piwheels.org/project/imagecodecs/>`_.
     See
     `issue 4721 <https://github.com/scikit-image/scikit-image/issues/4721>`_.

3. Linux on 64-bit ARM processors (NVidia Jetson):

   - Follow the conversation on
     `Issue 4705 <https://github.com/scikit-image/scikit-image/issues/4705>`_.

Although these platforms lack official support, many of the core
developers have experience with them and can help with questions.

If you want to install on an unsupported platform, the 
`developer instructions <how-to-contribute>`_  describe how to build from source.

Tell us which other platforms you'd like to see ``scikit-image`` on!
We are very interested in how ``scikit-image`` gets
`used <https://github.com/scikit-image/scikit-image/issues/4375>`_.

If you'd like to package ``scikit-image`` for as-yet-unsupported platform,
reach out on GitHub.

