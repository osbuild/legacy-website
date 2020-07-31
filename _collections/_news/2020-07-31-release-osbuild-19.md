---
caption: "Release of osbuild 19"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 19 of *osbuild*. After a rather long period
of development, this release comes with a wide range of new features and
improvements, as well as the usual round of bug fixes.

Below you can find the official changelog from the *osbuild-19* sources. All
users are recommended to upgrade!

----

  * osbuild is now warning if neither output-directory nor any
    checkpoints were specified on the command line. No attempt
    to actually build anything will be made.

  * Fix a bug in the `org.osbuild.files` source where the timeout
    was passed as a floating point value to curl, which in
    certain locales would result in a comma being used for the
    decimal separator, which can not be parsed by curl.

  * The `org.osbuild.systemd` stage gained the ability to mask
    services. Additionally, `enabled_services` is not a required
    option anymore.

  * The `org.osbuild.script` stage has been dropped.

  * The ability to pass in secrets via the command line has been
    removed. It was only used by the deprecated `dnf` stage.

  * The JSON schema was fixed for the `org.osbuild.noop` stage.

  * Stages and assemblers are now contained via `bubblewrap`
    instead of `systemd-nspawn`, which has many advantages,
    including but not limited to: being faster, not requiring
    root, better control of the contents of the build-root.

  * Internally, the logging of output and the communication
    between the stages and the osbuild process on the host has
    been reworked and cleaned up. This should allow better
    monitoring in the future.

  * The network of the sandbox that is used to run stages and the
    assemblers is now isolated from the host network.

  * As always, lots of improvements to the testing infrastructure,
    that should lead to better and quicker tests. Static analysis
    is run nightly as well.

Contributions from: Chloe Kaubisch, Christian Kellner, David Rheinsberg,
                    Major Hayden, Martin Sehnoutka, Ondřej Budai,
                    Tom Gundersen

— Berlin, 2020-07-30
