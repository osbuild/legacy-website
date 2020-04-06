---
caption: "Release of osbuild 10"
author: "David Rheinsberg"
categories: [fedoraplanet]
---
We are happy to announce version 10 of *osbuild*, again one of our regular
biweekly releases. Most of our efforts were spent on general cleanups and minor
documentation improvements. No big reworks or feature announcements this time.

Below you can find the official change log. Everyone is encouraged to upgrade!

----

## CHANGES WITH 10:

* A new man-page `osbuild-manifest(5)` is available, which describes
  the input format of the JSON manifest that `osbuild` expects.

* Man-pages can now be built via `make man`. This supports `SRCDIR` and
  `BUILDDIR` variables to build out-of-tree.

* Temporary objects in the object-store are now created in
  `.osbuild/tmp/`, rather than in the top-level directory. This should
  help cleaning up temporary objects after a crash. If no osbuild
  process is running, the `tmp/` subdirectory should not exist.

* The final stage of a build-pipeline is no longer automatically
  committed. You must pass checkpoints via `--checkpoint` to commit
  anything to the store.

* Improve curl timeout handling. This should improve osbuild behavior
  with slow or bad mirrors and make sure operations are retried
  correctly, or time-out if no progress is made.

Contributions from: Christian Kellner, David Rheinsberg, Lars Karlitski,
                    Major Hayden, Tom Gundersen

- Berlin, 2020-03-18
