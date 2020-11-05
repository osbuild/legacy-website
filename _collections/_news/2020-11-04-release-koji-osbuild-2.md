---
caption: "Second release of koji-osbuild"
author: "Christian Kellner"
categories: [fedoraplanet]
---
We are happy to announce the second release of *koji-osbuild*, the project
to integrate *osbuild-composer* with [koji](https://pagure.io/koji). This
is a bugfix release to fix issues uncovered after its first deployment.

Below you can find the official changelog from *koji-osbuild-2*.
All users are recommended to upgrade!

----

  * Fix the logic in the builder plugin that checks that
    all requested architectures for a requested build are
    indeed supported by the build tag. The existing check
    had its operands mixed up.

  * Fix the spec file so that the builder package now
    depends on python3-jsonschema.

  * Adapt the CI for a podman package change: previously
    the podman-plugins package, which contains the dnsname
    plugin, was automatically pulled in on Fedora. This
    changed recently which in turn broke our Fedora
    integration test. Explicitly install podman-plugins.

  * CI: Integrate codespell spell-checking.

  * Small fixes for the README.md.

Contributions from: Christian Kellner, Tomas Kopecek

— Berlin, 2020-11-03
