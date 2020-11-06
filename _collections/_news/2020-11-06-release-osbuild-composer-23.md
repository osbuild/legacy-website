---
caption: "Release of osbuild-composer 23"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released osbuild-composer 23 – better late
than never!

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* Support for building Fedora 31 images was removed.

* Metadata sent from Composer to Koji were adjusted based on a feedback from
  Koji maintainers. More fixes will definitely come in a future release.

* Composer is now easier to deploy to OpenStack with a new deploy-openstack
  script available in the source tree. Note that the previous version
  introduced a similar tool for deploying a local qemu VM.

* The testing setup is still being reworked massively. With the help of
  deploy-qemu, it should be now very simple to replicate the Schutzbot tests on
  a local machine.

Contributions from: Alexander Todorov, Lars Karlitski, Ondřej Budai, Tom
                    Gundersen, Xiaofeng Wang

— Liberec, 2020-11-04
