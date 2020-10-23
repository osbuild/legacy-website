---
caption: "Release of osbuild 23"
author: "Christian Kellner"
categories: [fedoraplanet]
---
We are happy to announce version 23 of *osbuild*. This release makes it
possible to build Fedora on RHEL systems.

Below you can find the official changelog from the *osbuild-23* sources. All
users are recommended to upgrade!

----

  * The `org.osbuild.rpm` stage now includes the `SIGPGP` and `SIGGPG`
    fields of each installed package in the returned metadata.
    Additionally, its docs have been improved to specify what metadata
    is returned.

  * The spec file has been changed so that the shebang for assemblers,
    stages and runners are not automatically mangled anymore. Runners
    were already changed to have the correct shebang for their target
    systems. Assemblers and stages are not meant to be run on the host
    itself, but always inside a build root container, which must bring
    the correct dependencies to run all stages and assemblers. For now,
    Python3 (>= 3.6), located at /usr/bin/python3, is required.
    This change will enable building Fedora systems on RHEL hosts.

  * Unit tests have been fixed to run on RHEL by dynamically selecting
    a runner that is suitable for the host system.

  * The stages unit tests are now using generated manifests via mpp,
    and have been updated to use Fedora 32. Additionally, the current
    mirror was replaced with [`rpmrepo`](https://osbuild.org/rpmrepo),
    which should provide a faster, more reliable package source.

  * The CI has dropped Fedora 31 but instead includes Fedora 33 as
    systems to run the composer reverse dependency tests for.

Contributions from: Christian Kellner, Lars Karlitski

— Berlin, 2020-10-23
