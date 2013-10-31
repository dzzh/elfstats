#Elfstats

**Elfstats** is a set of tools to parse web servers' access logs and visualize the data contained in them. This is a flexible monitoring solution for fine-grained tracking of the requests found in the logs using the regular expressions.

Elfstats code is written in Python programming language and can be installed either together with the other Python packages or completely separately in an own directory. Elfstats is built for Linux operating system (its compatibility with other POSIX-based OSes has not been tested yet) and can be installed either from source codes or from a set of RPM packages.

This is an umbrella repository for the elfstats project development. By now, it only  contains the sources of [elfstats.org](http://elfstats.org) web site (in its [gh-pages](https://github.com/dzzh/elfstats/tree/gh-pages) branch). Eventually, it will  include all elfstats-related repositories as the submodules and contain build scenarios for all-in-one elfstats installation.

##Components:

Elfstats project consists of a number of components that are located in their own repositories.

* [elfstats-env](https://github.com/dzzh/elfstats-env) -- an infrastructural repository containing Python virtual environment with all the needed dependencies. It is an optional component that simplifies the deployment procedure for the other components.
* [elfstatsd](https://github.com/dzzh/elfstats-env) -- a backend component aggregating data from web servers' logs and storing it in report files.
* [elfstats-munin](https://github.com/dzzh/elfstats-env) -- a set of [Munin](http://munin-monitoring.org) plugins visualizing the information obtained from *elfstatsd*.

## License

Elfstats is available under the terms of MIT License.

Copyright © 2013 [Źmicier Žaleźničenka][me] & Andriy Yakovlev.

Developed at [TomTom](http://tomtom.com). Inspired by [Oleg Sigida](http://linkedin.com/in/olegsigida/).

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

[me]: https://github.com/dzzh

