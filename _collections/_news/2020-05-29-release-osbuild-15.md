---
caption: "Release of osbuild 15"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 15 of *osbuild*. A handful of new features
and, as usual, lots of bugfixes all over.

Below you can find the official changelog from the *osbuild-15* sources. All
users are recommended to upgrade!

----

  * A new assembler, `org.osbuild.oci-archive`, that will turn a tree
    into an Open Container Initiative Image compliant archive. These
    archives can be used to run containers via e.g. podman.

  * Support for client side certificates to download content from the
    Red Hat servers: the `org.osbuild.files` source got support for
    reading entitlements and pass those certificates along when
    fetching content, i.e. RPMs.

  * A new ManifestPreProcessor (MPP) was added as a new tool located
    in `tools/mpp-depsolve.py`. Currently, it can take an existing
    manifest and dep-solve packages specified via a new `mpp-depsolve`
    option in existing `org.osbuild.rpm` stages.
    This is now used to generate Fedora 32 based test pipelines.

  * The `org.osbuild.ostree.commit` assembler gained an option to produce
    a tarball archive instead of emitting the plain OSTree repository.

  * Schema validation is now done with the draft 4 validator, and works
    therefore with pyhthon-jsonschema 2.6.

  * The `tree_id` and `output_id` fields got dropped from the resulting
    JSON when inspecting pipelines via `osbuild --inspect`.

  * The `--build-env` option has been dropped from the command line
    interface. It was deprecated and not used anymore.

  * Tests have been converted to not rely on `tree_id` and `output_id`
    anymore, as they are deprecated and will be removed in the future.

  * Lots of other improvements to the test infrastructure and the CI.

  * And finally for something meta: this file has been re-formatted to
    be proper markdown.

Contributions from: Christian Kellner, David Rheinsberg, Jacob Kozol,
                    Major Hayden

— Berlin, 2020-05-20
