libdnf
======

This library provides a high level package-manager. It's core library of [dnf](https://github.com/rpm-software-management/dnf), [PackageKit](https://github.com/hughsie/PackageKit) and [rpm-ostree](https://github.com/projectatomic/rpm-ostree). It's replacement for deprecated [hawkey library](https://github.com/rpm-software-management/hawkey) which it contains inside and uses [librepo](https://github.com/rpm-software-management/librepo) under the hood.

:warning: :warning: :warning:
**Note that libdnf is currently being reworked and is
considered unstable. Once major users like PackageKit and
DNF are fully ported, a new stable release will be
considered.**
:warning: :warning: :warning:

License
----

LGPLv2+

Building for Fedora
===================

Packages needed for the build, or the build requires:

* make
* check-devel
* cmake
* gcc
* libsolv-devel
* libsolv-tools
* librepo-devel
* python2-devel (or python3-devel for Python 3 build)
* python2-nose (or python3-nose for Python 3 build)
* rpm-devel
* sqlite-devel
* glib2-devel
* gtk-doc
* gobject-introspection-devel
* python2-sphinx (or python3-sphinx for Python 3 build)
* pygobject3-devel
* valgrind (optional)

From the checkout dir:

    mkdir build
    cd build/
    cmake .. # add '-DPYTHON_DESIRED="3"' option for Python 3 build
    make

Building the documentation, from the build/ directory::

    make doc

Building RPMs:

    tito build --rpm --test

Tests
=====

All unit tests should pass after the build finishes:

    cd build/tests
    make tests

There are two parts of unit tests: unit tests in C and unit tests in Python. To run the C part of the tests manually, from hawkey checkout::

    build/tests/test_main tests/repos/

Manually executing the Python tests::

    PYTHONPATH=`readlink -f ./build/src/python/` nosetests -s tests/python/tests/

The PYTHONPATH is unfortunately needed as the Python test suite needs to know where to import the built hawkey modules.

Documentation
=============

See the [hawkey documentation page](http://hawkey.readthedocs.org).

Information internal to the hawkey development is maintained on a [github wiki](https://github.com/rpm-software-management/dnf/wiki#wiki-Contact).

Useful links
============

Bug database:

 * [libdnf github issues](https://github.com/rpm-software-management/libdnf/issues)
 * [bugzilla](https://bugzilla.redhat.com/buglist.cgi?bug_status=NEW&bug_status=ASSIGNED&bug_status=POST&bug_status=MODIFIED&bug_status=ON_DEV&bug_status=ON_QA&bug_status=VERIFIED&bug_status=RELEASE_PENDING&bug_status=CLOSED&component=libdnf&list_id=8513553&product=Fedora&query_format=advanced)