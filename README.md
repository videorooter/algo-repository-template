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

Our test routines know of three ways in which to compile a project
from source. You're welcome to use either of them, but we have a
slight preference if you use `waf` as in the original blockhash
repository. The ways in which we can compile a source is:

 * `waf configure && waf` (if there's a `waf` file)
 * `make` (if there's a `Makefile`)
 * `prepare && make` (if there's a `prepare` file)

Usage
-----

For consistency, it's important your software always create a
binary in the `build/` directory named `blockhash`. It should accept
as arguments a list of images.

If your fork also work for videos, it should (additionally or instead
of) create a binary called `blockhash_video`. The existance of either
`blockhash` or `blockhash_video` will determine which tests to run.

The return value (on stdout) from the binary should always be the name
of the input file followed by whitespace (\t) followed by the hash
encoded in hexadecimal. There's no length requirement for the hash.

License
-------

Copyright 2016 Commons Machinery http://commonsmachinery.se/

Distributed under an MIT license, please see LICENSE in the top dir.

Contact: dev@commonsmachinery.se
