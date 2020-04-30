---
caption: "Release of osbuild 13"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce version 13 of *osbuild*, again one of our regular
biweekly releases.

Below you can find the official change log, compiled By Christian Kellner.
Everyone is encouraged to upgrade!

----

* Stage `org.osbuild.yum` has been dropped. It has been deprecated for some
  time and `org.osbuild.rpm` provides a better alternative.

* XZ compression now utilizes all available CPU cores. This affects all stages
  and assemblers that support XZ compression. It should decrease compression
  times considerably.

* `org.osbuild.grub2` now supports referring to file-systems via a label
  additionally to a UUID. This affects all places where an existing file-system
  is referred to. Disk creation still requires a UUID to be provided.
  `org.osbuild.fstab` gained similar support.

* RHEL-8.3 is now supported as host system.

* The 'libdir' layout in `/usr/lib/osbuild/` has been simplified. Distributions
  are no longer required to create mount anchors during installation. Instead,
  all modules (stages, assemblers, sources, and runners) can be copied verbatim
  from the source tree.

* `org.osbuild.grub2` now correctly pads `grubenv` files to 1024 bytes. This
  was not done correctly, previously, and caused other parsers to fail.

* The containerization via systemd-nspawn was adjusted to support running in a
  container. With sufficient privileges, you can now run osbuild pipelines from
  within a container.

Contributions from: Christian Kellner, David Rheinsberg, Major Hayden

- Berlin, 2020-04-29
