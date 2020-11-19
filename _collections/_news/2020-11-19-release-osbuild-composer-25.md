---
caption: "Release of osbuild-composer 25"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released [osbuild-composer 25][1]. It now
supports building RHEL 8.4. 🤗

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* Composer now supports RHEL 8.4! Big thanks to Jacob Kozol! If you want to
  build RHEL 8.4 using Composer API or Composer API for Koji, remember to pass
  "rhel-84" as a distribution name.

* Composer can now be started without Weldr API. If you need it, start
  `osbuild-composer.socket` before `osbuild-composer.service` is started. Note
  that cockpit-composer starts `osbuild-composer.socket` so this change is
  backward compatible.

* When Koji call failed, both osbuild-composer and osbuild-worker errored. This
  is now fixed.

* The dependency on osbuild in the spec file is now moved to the worker
  subpackage. This was a mistake that could cause the worker to use an
  incompatible version of osbuild.

* As always, testing got some upgrades. This time, mostly in the way we build
  our testing RPMs.

Contributions from: Jacob Kozol, Lars Karlitski, Ondřej Budai, Tom Gundersen

— Liberec, 2020-11-19

[1]: https://github.com/osbuild/osbuild-composer/releases/tag/v25
