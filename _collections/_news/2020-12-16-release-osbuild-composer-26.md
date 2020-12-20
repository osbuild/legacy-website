---
caption: "Release of osbuild-composer 26"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released [osbuild-composer 26][1].

It now allows sharing Amazon Machine Images with another account after
uploading. This is useful when you run osbuild-composer for others: they don't
need to pass AWS secrects to your instance, but only an account id.

The composer API gained support for dnf's `mirrorlist` and `metalink` URLs,
making building from official Fedora repositories easier.

It also contains many updates to the RHEL 8.4 images we introduced in the last
release, as well as bug fixes and stability improvements.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* RHEL 8.4 images got plenty of updates:
  * Image building for aarch64, ppc64le and s390x is fixed.
  * The root XFS partition now has a random UUID. This change fixes image
    builds on an image built by osbuild-composer.
  * QCOW2 images are now closer to the old official ones:
    * The default size is now set to 10 GiB.
    * rng-tools are no longer installed.
    * kernel options are now aligned to the old official images.
  * org.osbuild.rhel84 runner is now used to build these images.

* Worker crashed in a koji-finalize job when a previous koji-init job failed.
  This is now fixed.

* Composer API has now support for mirrorlist and metalink.

* Composer API now supports sharing an Amazon Machine Image with an another
  account.

* Upload of aarch64 images to AWS is now fixed.

* Composer API for Koji returns pending status until all images are finished.
  Previously, it returned failed as soon as the first image build failed.

* Composer API for Koji and Worker API now log errors. This should very much
  simplify debugging.

* osbuild-composer(7) man page is now included in the RPM.

* The testing got some very nice updates too:
  * The CI now runs a subset of tests on Fedora 33 aarch64.
  * The CI now runs reverse dependency tests against koji-osbuild.

Contributions from: Chloe Kaubisch, Christian Kellner, Jacob Kozol,
                    Lars Karlitski, Ondřej Budai, Sanne Raymaekers,
                    Tomas Hozza

— Liberec, 2020-12-16

[1]: https://github.com/osbuild/osbuild-composer/releases/tag/v26
