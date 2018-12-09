Contributing Guidelines
=======================

Contributions are very welcome! This includes not only new features, but bug
reports and documentation. Please follow the guidelines laid out below.

When contributing to this repository, please first discuss the change
you wish to make via an “issue”. The issue will be used as a forum of
discussion for the bug, feature or update before merging the changes.

This project follows the `Git Feature Branch
Workflow <https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow>`__
for any new features/bugs/updates.

Table of Contents
-----------------

-  `Setting up Development
   Environment <#setting-up-development-environment>`__
-  `Running Tests <#running-tests>`__
-  `Raising an Issue <#raising-an-issue>`__
-  `Pull Request Process <#pull-requests>`__

Setting Up Development Environment
----------------------------------

The bare minimum you'll need to work on the TIFlash project is:

- Python (preferably 3.6.6+)
- Code Composer Studio (preferably latest)
- a Texas Instruments Device

To get yourself set up and running ASAP, we recommmend using the provided
Vagrantfile and provisioning scripts to spin up a vm set up for development.
For this you'll need:

- `Vagrant <https://www.vagrantup.com/>`__
- `VirtualBox <https://www.virtualbox.org/>`__
- `Ansible <https://www.ansible.com/>`__

::

    # clone repo and cd into directory
    git install https://github.com/webbcam/tiflash.git && cd tiflash

    # create vm and ssh into it
    vagrant up
    vagrant ssh

    # the repo will be sync'd with the vm folder '/develop'
    cd /develop     # do all work here

    # install tiflash via pip in edit/develop mode
    pip install -e .

    # setup pre-commit hooks (style guide testing)
    cd hooks
    chmod +x install-hooks.sh pre-commit.sh
    ./install-hooks.sh

Running Tests
-------------

Before creating any pull requests you should be sure to run the tests
(located in `tests <tests>`__ directory) locally.

Please see the `README.rst <tests/README.rst>`__ for further instructions.

Raising an Issue
----------------

Please raise an issue for any bug, new feature or updates. You should
use the `ISSUE_TEMPLATE.md <ISSUE_TEMPLATE.md>`__ as a starting place
for your issue.

Pull Requests
-------------

When preparing a pull request you should run through the following
steps:

1. Run entire test suite on your local PC with the new changes and
   include report.html (generated with pytest-html plugin) with pull
   request.
2. Update the appropriate README.md with details of changes to the
   project. This includes any new feature added, any new tests added
   (and expected result) for fixed bug, etc.
3. Increase the version numbers in any examples files and the README.md
   to the new version that this Pull Request would represent. The
   versioning scheme we use is `SemVer <http://semver.org/>`__.
4. You may merge the Pull Request in once you have the sign-off of two
   other developers, or if you do not have permission to do that, you
   may request the second reviewer to merge it for you. Note all tests
   must pass on our test setup before Pull Request can be merged.

