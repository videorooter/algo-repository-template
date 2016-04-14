algo-repository-template
========================

This is a template for any algorithms developed in line with the
Videorooter initiative. If you fork this repository (or one of the
other source directories listed below), our testing system will
automatically detect the fork and include it in our automated testing.

For this to work, your fork needs to compile. If you require anything
other than a standard build environment, your fork may fail to build
on the image we use. You can see the Dockerfile we use to build the
environment in the utility/docker directory of the
videorooter/test-routines git repository:

  https://github.com/videorooter/test-routines/blob/master/utility/docker/Dockerfile

If you require different tools in your build environment which does
not conflict, you can make the change to the Dockerfile and make a
pull request so we can include it.

Source directories
------------------

At the moment, our scripts watch the following Github repositories for
forks:

 * https://github.com/videorooter/algo-repository-template
 * https://github.com/commonsmachinery/blockhash

Build and install
-----------------

Our test routines are flexible as to how to compile a project
from source. You're welcome to use any means necessary, but we have a
slight preference if you use `waf` as in the original blockhash
repository. In your repository, you must have a file called
`videorooter.conf` which is sourced by our test scripts to set some
variables and define functions for building and executing.

You can look at the `videorooter.conf` included in this repository for
inspiration. The following functions must exist:

 * `compile` called without arguments to compile a prestine source
 * `calc` called with (image, movie) as the first argument and a
   filename as the second argument, to calculate the fingerprint of a
   file.

The following variables must be defined:

 * `images` set to 1 if the repository support images
 * `movies` set to 1 if the repository support movies

Usage
-----

The return value (on stdout) from a call to `calc` should always be the name
of the input file followed by whitespace (\t) followed by the hash
encoded in hexadecimal. There's no length requirement for the hash.

License
-------

Copyright 2016 Commons Machinery http://commonsmachinery.se/

Distributed under an MIT license, please see LICENSE in the top dir.

Contact: dev@commonsmachinery.se
