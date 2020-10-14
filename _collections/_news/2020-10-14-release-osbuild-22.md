---
caption: "Release of osbuild 22"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 22 of *osbuild*. This release improves the
internal error-handling as well as error-reporting on the command-line.

Below you can find the official changelog from the *osbuild-22* sources. All
users are recommended to upgrade!

----

  * runners: support for RHEL 8.4 was added

  * A new internal API was added that can be used to communicate
    exceptions from runners, stages and assemblers in a more
    structured way and, thus, make it possible to include them in
    the final result in a machine readable way. Use that new API
    in the runners.

  * Improvements to the CI, including the integration of codespell
    to check for spelling mistakes.

Contributions from: Chloe Kaubisch, Christian Kellner, Jacob Kozol,
                    Lars Karlitski, Major Hayden

— Berlin, 2020-10-08
