---
caption: "Release of osbuild 11"
author: "Lars Karlitski"
---
We are happy to announce version 11 of *osbuild*, again one of our regular
biweekly releases. Most of our efforts were again spent on general cleanups and
minor documentation improvements. No big reworks or feature announcements this
time.

Below you can find the official change log, compiled By Christian Kellner.
Everyone is encouraged to upgrade!

----

## CHANGES WITH 11:

* Drop support for legacy input: passing in non-manifest style pipelines is now
  not supported anymore.

* Support for specifying an UUID for partitions when using the GPT partition
  layout was added to the org.osbuild.qemu assembler.

* Fix a crash in the case the assembler failed, which was caused by cleanup up
  the object while the object was still being written to.

* Delay the cleanup of the build tree to after the error checking since in the
  error case there is nothing to clean up and trying to do so will lead to
  crash.

* `objectstore.Object` now directly cleans its working tree up, in contrast to
  relying on the implicit cleanup of `TemporaryDirectory`.  One advantage of
  this is that the custom cleanup code can handle immutable directories, which
  Python 3 fails to clean up.

* Drop custom `os-release` creation from the RHEL 8.2 runner. The issue that
  made this neccessary got fixed upstream.

* Ensure the build tree is always being built even if there are no stages
  specified.

* spec file: Do no generate dependencies for the internal files and add NEWS.md
  to the documentation section.

* The Fedora 30 based aarch64 example was fixed and now builds again.

Contributions from: Christian Kellner, David Rheinsberg, Lars Karlitski, Major
Hayden, Martin Sehnoutka, Ondřej Budai

-- Berlin, 2020-04-01
