---
caption: "Release of osbuild-composer 13"
author: "Ondřej Budai"
categories: [fedoraplanet]
---

Yesterday, we released version 13 of *osbuild-composer*. We are very proud of
this release as it contains lots of very nice improvements. The most important
ones are: support for building Fedora IoT commit tarballs, revamped support
for RHEL 8 and dropping the ability to build Fedora 30 and several poorly-
defined image types.

But there’s much more, see the list of changes below. An upgrade is highly
recommended!

----

* Fedora IoT is now supported for Fedora 32 in the form of producing the
  commit tarball. Feel free to test it and report any issues you find.

* Support for RHEL was completely revamped. Now, osbuild-composer supports
  building images only for the latest RHEL 8. The separate minor versions
  are no longer available. Additionally, it now uses the Red Hat CDN which
  requires the host system to be properly subscribed. If you need to use
  different package repositories to build RHEL from, use a repository
  override in /etc/osbuild-composer/repositories.

* Several image types were removed: ext4-filesystem, partitioned-disk,
  and tar. The use-cases for these image types were not clearly defined and
  without a clear definition, it was very hard to define test cases for
  them.

* Support for Fedora 30 was dropped as it is now EOL. So long and thanks
  for all the fish!

* The timeout for AWS upload is removed. It's very hard to predict how long
  will the AWS upload take. With the timeout in place, it caused the test
  suite to produce a lot of false positives.

* Build logs were broken in the previous release, this release fixes it.
  This time, they were properly saved but weldr API read them from a wrong
  location. This is now fixed and covered with basic tests.

* Weldr API has now support for /compose/metadata and /compose/results
  routes. This allows users to easily access a manifest used to build
  an image.

* Preliminary support for ppc64le and s390x is added to RHEL distribution.
  No images cannot be built yet but at least it won't crash on startup.

* The weldr API socket has now correct permissions. As the result, it can
  be read and written only by root and the weldr group. This is the same
  behaviour as Lorax has.

* By mistake, workers incorrectly used the default store for every build.
  However, this can currently cause the store to grow indefinitely, so
  this release switched the osbuild store to use a temporary directory again.

* /status route in weldr API now correctly returns msgs field.

* Handling of json (un)marshalling in store is revamped. It should
  make it more stable and simplify the maintenance of the store backwards
  compatibility.

* Initial support for koji is now added. It's currently not hooked up
  to composer and only supports password authentication. More coming soon.

* Again, the automated testing was greatly improved during this cycle,
  big thanks to everyone involved!

Contributions from: Alexander Todorov, Brian C. Lane, David Rheinsberg, Jacob
                    Kozol, Lars Karlitski, Major Hayden, Ondřej Budai, Tom
                    Gundersen


— Liberec, 2020-05-28
