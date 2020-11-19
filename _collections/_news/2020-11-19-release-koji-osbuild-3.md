---
caption: "Release of koji-osbuild 3"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released [*koji-osbuild* 3][1], our new project to
integrate *osbuild-composer* with [koji](https://pagure.io/koji), the build and
tracking system primarily used by the Fedora Project and Red Hat.

Below you can find the official change log, compiled by Christian Kellner.

----

* Ship tests in koji-osbuild-tests package. The tests got reworked so that they
  can be installed and run from the installation. This will be useful for
  reverse dependency testing, i.e. testing the plugins from other projects,
  like composer as well as in gating tests.

* Add the ability to skip the tagging. An new command line option, --skip-tag
  is added, which translate into an a new field in the options for the hub and
  builder. If that option is present, the builder plugin will skip the tagging
  step.

* builder plugin: the compose status is attached to the koji task as
  compose-status.json and updated whenever it is fetched from composer. This
  allows to follow the individual image builds.

* builder plugin: The new logs API, introduce in composer version 24, is used
  to fetch and attach build logs as well as the koji init/import logs.

* builder plugin: Support for the dynamic build ids, i.e. don't use the koji
  build id returned from the compose request API call but use the new
  koji_build_id field included in the compose status response. This makes
  koji-osbuild depend on osbuild composer 24!

* test: lots of improvements to the tests and ci, e.g. using the quay mirror
  for the postgres container or matching the container versions to the host.

Contributions from: Christian Kellner, Lars Karlitski, Ondřej Budai

— Berlin, 2020-11-19

[1]: https://github.com/osbuild/koji-osbuild/releases/tag/v3
