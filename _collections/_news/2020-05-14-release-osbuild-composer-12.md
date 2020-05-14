---
caption: "Release of osbuild-composer 12"
author: "Ondřej Budai"
categories: [fedoraplanet]
---
Today, we released version 12 of *osbuild-composer*. This time, there are no
major features. However, you are still encouraged to upgrade because the new
version contains a lot of fixes and refactorings making the tool more stable.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* In previous versions support for running remote workers was broken. This is
 now fixed and running remote workers is once again possible. See #568 for
 more information.

* The job queue and the store are now two separate Go packages. One of
 the benefits is that it is now possible to build images without using
 the store which is too complicated for some usecases.
 
* A blueprint name is now checked against the regex "^[a-zA-Z0-9._-]+$". This
 is the same limitation as in lorax-composer.
 
* All osbuild calls now use the new --output-directory argument. This change
 is a must because the old way of retrieving images from the osbuild store
 will soon be deprecated.
 
* Some routes from the weldr API are now implemented in a more efficient way.
 
* As always, the team worked hard on improving the tests and the CI.

Contributions from: Brian C. Lane, David Rheinsberg, Jiri Kortus,
                    Lars Karlitski, Major Hayden, Ondřej Budai

- Liberec, 2020-05-13
