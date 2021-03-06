#--------------------------------------------------------------------------
# File and Version Information:
#  $Id: README 4 2008-10-08 19:27:36Z salnikov $
#
# Description:
#  README file for package CodeGen
#------------------------------------------------------------------------

Package author: Andrei Salnikov

Brief description:
==================

Package codeGen is for the script(s) which generate templates for the new
classes or plain files.

Detailed description:
=====================

Main item in the package is the `codegen' script which is run by the end
users of the package to produce the template for the new classes or
other types of files. Codegen supports several programming languages and
in some cases several types of classes or files for one language. For
simplicity all different types of output are considered as different
"languages".  Examples of such languages could be "C++" and "C++-template".
Former means ordinary non-template C++ class, while latter is used to
generate template C++ class.

To get a complete list of supported types of ouput (languages) one can use
this command:

    % codegen -p
    C++
    C++-template
    ChangeLog
    README
    python
    python-main

To generate the template file(s) for the new C++ class one can use this
command:

    % codegen -l C++ MyPackage MyClass

The output of this command - two files MyClass.h and MyClass.cpp - will be
placed in the current directory, one has to copy files to their final
location manually. If there are already files with the same name in the
current directory the script will not override them. The "-l C++" is optional,
by default script generates code for non-template C++ classes.

Few other examples:

- generate non-template C++ class with base class name "Base":
    
    % codegen -b Base MyPackage MyClass

- generate C++ class with base class name "Base" from package "BasePackage":
    
    % codegen -b BasePackage/Base MyPackage MyClass

 - generate templated C++ class:
    
    % codegen -l C++-template MyPackage MyClass

    (generated class has only one template parameter <typename T>)

- generate Python module for a class MyClass with base class "object":
    
    % codegen -l python -b object MyPyPackage MyPyClass

    (output will be in a MyPyClass.py file)

- generate script containing "main()" function (executable script):
    
    % codegen -l python-main MyPyPackage MyPyScript
