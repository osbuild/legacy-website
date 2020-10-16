---
caption: "Release of osbuild-composer 22"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released osbuild-composer 22.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* Support for building Fedora 33 images is now available as a tech preview.

* The osbuild-composer-cloud binary is gone. The osbuild-composer binary
now serves the Composer API along with Weldr and Koji APIs.

* The testing setup was reworked. All files related to tests are now shipped
in the tests subpackage. A script to run the test suite locally is now
also available. See HACKING.md for more details.

* GPG keys in Koji API are no longer marked as required.

* Osbuild-composer RPM is now buildable on Fedora 33+ and Fedora ELN.

* Osbuild-composer for Fedora 34 and higher now obsoletes lorax-composer.

Contributions from: Alexander Todorov, Jacob Kozol, Lars Karlitski,
                    Martin Sehnoutka, Ondřej Budai, Tom Gundersen

— Liberec, 2020-10-16

