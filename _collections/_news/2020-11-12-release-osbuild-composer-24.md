---
caption: "Release of osbuild-composer 24"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce that we released osbuild-composer 24.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* Composer now internally supports multi-build composes. A big part of the
jobqueue and worker was rewritten to support this feature.

* Composer API for Koji was adjusted to use the new multi-build feature. All
communication with Koji was moved to the worker so there's no need to have Koji
credentials in composer (it's sufficient to have them in the worker).
Additionally, the API can now correctly handle requests with multiple images.

* Composer API for Koji has now /compose/{id}/logs route exposing logs to a
caller. Keep in mind that the API specification doesn't guarantee the field
structure, so it may change at any point in the future.

* Composer API returned statuses that were not defined in the API specification.
This is now fixed.

* As always, there we are improvements in the testing pipeline. The biggest
change is the introduction of Fedora 33 in composer's CI.

Contributions from: Chloe Kaubisch, Lars Karlitski, Martin Sehnoutka,
                    Ondřej Budai, Tom Gundersen

— Liberec, 2020-11-11
