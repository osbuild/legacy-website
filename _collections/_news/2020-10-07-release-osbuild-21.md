---
caption: "Release of osbuild 21"
author: "Christian Kellner"
categories: [fedoraplanet]
---
We are happy to announce version 21 of *osbuild*. This release adds
support for running on Fedora 34. Furthermore, internal errors during
container setup are now properly reported. And lastly, a lot of work has
been done to improve the code readability.

Below you can find the official changelog from the *osbuild-21* sources. All
users are recommended to upgrade!

----

  * The way that output of modules is communicated to osbuild was
    re-factored in a way that now makes it possible to also capture
    and log the output of the container runtime, i.e. `bubblewrap`.
    This should prove useful to track down errors where the runner
    can not be executed.

  * runners: support for Fedora 34 was added

  * A lot of internal re-factoring was done, to make the code nicer
    and easier to read. For example the way objects are exported in
    the pipeline is now unified.
    Additionally, a dedicated API is used to fetch the arguments in
    the modules, instead of relying on standard input.

Contributions from: chloenayon, Christian Kellner

— Berlin, 2020-09-10
