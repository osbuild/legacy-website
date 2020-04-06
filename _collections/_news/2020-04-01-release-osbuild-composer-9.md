---
caption: "Release of osbuild-composer 9"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce version 9 of *osbuild-composer*, again one of our
regular biweekly releases.

The most visible changes are that we're building up-to-date Fedora images now
by including the *updates* repositories and that we're releasing into Fedora 32
and 33 under a new—less confusing—package name: *osbuild-composer*.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

## CHANGES WITH 9:

* Fedora is now build with updates and modules repositories enabled, therefore
  up-to-date images are now produced.

* A new man-page `osbuild-composer(7)` with high-level description of the
  project is now available. It can be built by the new man target in the
  Makfile.

* All Fedora images have now a generic initramfs. This should make the images
  more reproducible and less likely failing to boot if the image build was done
  in a less usual environment.

* Metalink is now used to access the Fedora repositories. This change should
  hopefully lead to more stable builds.

* Composer is now released to Fedora 32 and 33 in a new osbuild-composer
  package. The old golang-github-osbuild-composer package will be automatically
  upgraded to the new one.

* The internal osbuild-pipeline command now has a more user-friendly interface.

* The RCM API (in development, experimental) is reworked to allow any
  distribution-architecture-image type combination.

* The work on a high-level description of image types began.  See image-types
  directory.

* The osbuild-worker arguments are reworked, they are now much more flexible.

* The image-info tool used in the integration tests can be now run on Fedora
  32.

* The unit test coverage is now much bigger, thanks to all contributors!

* Internal distribution representation is significantly reworked, this
  simplifies the process of adding the support for all currently missing
  architectures.

* Integration tests were also improved, the image tests are fully switched to
  the new Go implementation and an automatic way of generating test cases is
  added. The weldr API coverage is also much better. Several bugs in it were
  fixed in the process.

* Codecov.io is now used to monitor the test coverage of the code.

* As always, minor fixes and improvements all over the place.

Contributions from: Alexander Todorov, Brian C. Lane, David Rheinsberg, Jacob
Kozol, Jakub Rusz, Jiri Kortus, Lars Karlitski, Martin Sehnoutka, Ondřej Budai,
Tom Gundersen

-- Liberec, 2020-04-01
