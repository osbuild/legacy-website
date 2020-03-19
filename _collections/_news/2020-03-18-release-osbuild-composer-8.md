---
caption: "Release of osbuild-composer 8"
author: "David Rheinsberg"
---
We are happy to announce version 8 of *osbuild-composer*, again one of our
regular biweekly releases.

The biggest change is that we now use the `org.osbuild.rpm`
stages, rather than `org.osbuild.dnf`. This makes the dependency resolution of
package installations a lot simpler and cleaner. This should not have any user
visible effects, other than reduced build-times and slightly different pipeline
output.

Below you can find the official change log. Everyone is encouraged to upgrade!

----

## CHANGES WITH 8:

* All generated pipelines now use the rpm stage rather than the dnf stage.

* The state directory can be now set using `STATE_DIRECTORY` env variable.

* Several fixes in blueprint weldr API.

* Mising systemd scriplets were added to the spec file.
