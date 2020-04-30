---
caption: "Release of osbuild-composer 11"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce version 11 of *osbuild-composer*, again one of our
regular biweekly releases. It now supports uploading images to Azure as well.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* The support for uploading VHD images to Azure is now available.

* AMI images are now produced in the vhdx format. This fixes the issue that
  those images couldn't be previously booted in EC2.

* In version 10 the logs weren't saved when osbuild failed. This is now fixed.

* The warnings when upgrading/removing the RPM package are now fixed. Note that
  updating to version 11 still produces them because the upgrade process runs
  also the scriptlets from version 10.

* The size calculation for Fedora 31 vhd images is fixed.

* The size field was removed from the tar assembler struct. The field has
  actually never been supported in osbuild and it doesn't make any sense.

* The minimal required version of osbuild is bumped to 12.

* This release also got big upgrades to the testing infrastructure, more tests
  are run on a CI and they now run faster. Also, the unit test coverage is
  improved.

Contributions from: Alexander Todorov, Jacob Kozol, Jakub Rusz, Jiri Kortus,
Lars Karlitski, Major Hayden, Ondřej Budai, Tom Gundersen

- Liberec, 2020-04-29
