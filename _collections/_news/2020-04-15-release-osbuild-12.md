---
caption: "Release of osbuild 12"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce version 12 of *osbuild*, again one of our regular
biweekly releases.

This release adds multiple stages and sources for building OSTree-based
systems. See `samples/f31-ostree-*.json` for examples how to use it.

It also drops support for the `org.osbuild.dnf` source and stage. Please use
the rpm stage instead.

Below you can find the official change log, compiled By Christian Kellner.
Everyone is encouraged to upgrade!

----

* The `qemu` assembler now supports the `VHDX` image format. This is the
  preferred format for AWS targets, so it is a natural fit for our assemblers.

* The `grub2` stage now disables the legacy compatibility by default.  You have
  to explicitly enable it in the stage options if you require it.

* Additionally, the `grub2` stage now also has a `uefi.install` option to
  control whether it installs the UEFI configuration from the build tree into
  the target tree. Furthermore, a new option called `write_defaults` controls
  whether default options are written to `/etc` (enabled by default).

* The `dnf` stage was removed. The `rpm` stage fully replaces all its
  functionality.

* The `fedora27` runner is no longer supported. Fedora 30 is the minimum
  required host version for Fedora systems.

* Add OSTree integration. This includes multiple stages and sources which allow
  to export osbuild trees as ostree commits, or import ostree commits into an
  osbuild pipeline:

  * org.osbuild.rpm-ostree: This stage uses `rpm-ostree compose` to post-process
    a tree and prepare it for committing to ostree.

  * org.osbuild.ostree.commit: A new assembler that takes a tree that conforms to
    the ostree layout and turns it into an ostree commit.

  * org.osbuild.ostree: A new source that provides external ostree commits to a
    pipeline.

  * org.osbuild.ostree: A new stage that takes an ostree commit and prepares the
    working directory with its content.

* The `osbuild` binary now has an `--output-directory=DIR` argument which
  allows to specify a directory where to put the output of the pipeline
  assembler. This is optional for now, but will be made mandatory in the
  future.

* A new stage called `org.osbuild.first-boot` allows to control the execution
  of scripts at the first bootup of the generated images.

Contributions from: Christian Kellner, David Rheinsberg, Major Hayden, Ondřej
Budai, Tom Gundersen

- Berlin, 2020-04-15
