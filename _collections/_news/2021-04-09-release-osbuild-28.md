---
caption: "Release of osbuild 28"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 28 of *osbuild*. This time with a large set of
fixes and minor additions to the different stages bundled with osbuild.
Furthermore, Fedora 35 is now supported as host system.

Below you can find the official changelog from the *osbuild-28* sources. All
users are recommended to upgrade!

----

 * Add a new option to the `org.osbuild.qemu` assembler that controls
   the qcow2 format version (`qcow2_compat`).

 * Add history entries to the layers of OCI archives produced by the
   `org.osbuild.oci-archive` stage. This fixes push failures to quay.io.

 * Include only a specific, limited set of xattrs in OCI archives produced by
   the `org.osbuild.oci-archive` stage. This is specifically meant to exclude
   SELinux-related attributes (`security.selinux`) which are sometimes added
   even when invoking  `tar` with the `--no-selinux` option.

 * The package metadata for the `org.osbuild.rpm` stage is now sorted by
   package name, to provide a stable sorting of the array independent of
   the `rpm` output.

 * Add a new runner for Fedora 35 (`org.osbuild.fedora35`) which is
   currently a symlink to the Fedora 30 runner.

 * The `org.osbuild.ostree` input now uses `ostree-output` as temporary
   directory and its description got fixed to reflect that it does
   indeed support pipeline and source inputs.

 * devcontainer: Include more packages needed for the Python extension and
   various tools to ease debugging and development in general. Preserve
   the fish history across container rebuilds.

 * Stage tests are writing the prodcued metadata to `/tmp` so the actual
   data can be inspected in case there is a deviation.

 * CI: Start running images tests against 8.4 and execute image_tests directly
   from osbuild-composer-tests. Base CI images have been updated to Fedora 33.

Contributions from: Achilleas Koutsou, Alexander Todorov, Christian Kellner,
                    David Rheinsberg

— Berlin, 2021-04-08
