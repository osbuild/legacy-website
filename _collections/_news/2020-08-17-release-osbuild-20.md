---
caption: "Release of osbuild 20"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 20 of *osbuild*. This time with a big set
of new features, including support for *btrfs* assemblers, as well as reworked
and improved progress output on the terminal. As usual, a round of bugfixes is
included as well.

Below you can find the official changelog from the *osbuild-20* sources. All
users are recommended to upgrade!

----

  * The filesystem assemblers gained support for btrfs. They can
    now output image files as btrfs, similar to the existing support
    for ext4 and xfs.

  * The `--libdir=DIR` handling was generalized in that an empty
    `osbuild` subdirectory will now always cause osbuild to use the
    system osbuild package. This means a custom `libdir` via
    `--libdir=DIR` no longer requires the entire osbuild python
    package to be bundled in an `osbuild` subdirectory.

  * When run on a terminal, `osbuild` will now output the duration
    of a stage (or other module).

  * The `--output-directory` switch is now mandatory if no checkpoint
    was specified. In this situation, running `osbuild` would be a
    no-op.

  * The `ostree` assembler now optionally emits version metadata in
    its commits.

  * `osbuild` now supports running on Ubuntu-20.04.

  * Modules can now pass metadata alongside the filesystem objects
    they emit. This metadata is not stored in the final artifact, but
    passed to the caller via the structured osbuild output.

  * The `ostree` assembler now emits compose metadata as part of its
    build. This can be inspected by the caller to get detailed compose
    information.

  * The `rpm` stage now emits detailed metadata about the installed
    RPM packages.

  * Lots of fixes all over the place, including SELinux reworks and
    PEP-8 conformance.

Contributions from: Christian Kellner, David Rheinsberg, Davide Cavalca,
                    Major Hayden, chloenayon

— Berlin, 2020-08-13
