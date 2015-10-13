[![Build Status](https://travis-ci.org/drewsonne/pyvagrantconfig.svg?branch=master)](https://travis-ci.org/drewsonne/pyvagrantconfig)

# pyvagrantconfig
Parses a vagrant file into a python object for inspect. Mainly used to read and build Vagrant file in python.
I built this to help me write a utility in python which can build projects and convert Vagrantfiles to packer files.

## Supported Directives

 - Most vm.config directives,
 - Chef provisioner
 - Shell provisioner
 - VB provider

## Deployment
When this is ready to be deployed, you can upload it to the nordcloud pip server

    $ cd $WORKSPACE/pyvagrantconfig
    $ python setup.py sdist upload

## Installation
After it's on the nordcloud pip server, you should be able to install on the client by running

    $ pip install pyvagrantconfig

## Usage

## Contributing
If someone were to modify this utility, is there anything important about it that they should know?
### virtualenv
When doing development and testing, it's good practice to use a virtualenv. A virtualenv is a sandboxed python environment which does not modify the system python installation
You can install one as follows:

    $ pip install virtualenv
    $ cd $WORKSPACE/pyvagrantconfig
    $ virtualenv venv
    $ . ./venv/bin/activate
    (pyvagrantconfig)$

Now that you have a working virtualenv, you can install the utility in development mode. Keep in mind that the 'activate' step, is valid only for a single session. If you close the terminal
you'll have to run `venv/bin/activate` again. You can now run pip, python, and pyvagrantconfig while only referring to the local python environment created in $WORKSPACE/pyvagrantconfig. You can see this by running:

    (pyvagrantconfig)$ which pip
    $WORKSPACE/pyvagrantconfig/venv/bin/python
    (pyvagrantconfig)$ which python

### Development Mode
When testing this utility, you can install it and still edit the source files as follows:

    $ cd $WORKSPACE/pyvagrantconfig
    $ pip install --editable .

### Roadmap
I intially tried to use pyPEG, but could not get a handle on it, so for now, we use a custom state parser.
I want to move this to a PEG parser to make it easier to manage, but in the spirit of minimum viable product, it's up and out.

 - This is currently way too specific. Needs to be rewritten to parse general ruby structures and extract details out of it, rather than looking for particular vagrant configurations.
 - Port parser from state parser to PEG parser.