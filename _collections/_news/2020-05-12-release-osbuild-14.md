---
caption: "Release of osbuild 14"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
Last week, we released version 14 of *osbuild*. It is a regular release with a
handful of new features, as well as a bunch of fixes. The major new feature is
support for input-validation via JSON-schemata, as well as the `--inspect`
command-line option to get more information about manifests without running the
pipeline engine.

This release is one week early, but we intend to continue bi-weekly releases.
However, from now on *osbuild* and its dependents (including *osbuild-composer*)
will release alternatingly.

Below you can find the official changelog from the *osbuild-14* sources. Go
forth and fetch it while it is hot!

----

* Schema validation: The osbuild python library gained support for
  retrieving the metadata of modules and schema validation. This is
  being used on each invocation of osbuild in order to validate the
  manifest. Should the validation fail the build is aborted and
  validation errors are returned, either in human readable form or
  in JSON, if `--json` was specified.

* A `--inspect` command line option was added for osbuild. Instead
  of attempting to build the pipeline, the manifest will be printed
  to stdout in JSON form, including all the calulcated identifiers
  of stages, the assembler and the `tree_id` and `output_id` of the
  pipeline (and build pipelines). Schema validation will be done and
  errors will be reported.

* Internally, the buildroot class now uses `PYTHONPATH` to point to
  the `osbuild` module instead of the symlinks or bind-mounts in the
  individual modules.

* Fixes to the CI and many cleanups to the schemata, sample and test
  pipelines as a result of the schema validation work.

Contributions from: Christian Kellner, David Rheinsberg, Ondřej Budai

- Berlin, 2020-05-06
