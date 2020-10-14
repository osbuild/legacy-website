---
permalink: /rpmrepo/
---
# RPM Repository Snapshots

For reliable continuous development, the OSBuild project employs its own RPM
repository snapshots. These snapshots are persistent and immutable. They are
meant to be used by test farms, CI systems, and other development tools, in
case the official RPM repositories are not suitable.

---

**WARNING**: _These snapshots are not meant for production use! No guarantee of
safety, applicability, or fitness for a particular purpose is made. No security
fixes are applied to the repositories!_

---

## Repositories

An enumeration of all available snapshots can be retrieved via:

    $ curl https://rpmrepo.osbuild.org/control/snapshots | jq .

The following table lists the repositories that are snapshotted, as well as the
availability guarantees, and the different variants.

---

| Platform      | Version | Architectures                    | Lifetime |
| ------------- |:-------:|:--------------------------------:| -------- |
| Fedora        | 31      | x86\_64                          | 6 months |
| Fedora        | 32      | x86\_64                          | 6 months |
| Fedora        | 33      | x86\_64                          | 6 months |
| RHEL          | 8.2     | aarch64, ppc64le, s390x, x86\_64 | 6 months |
| RHEL          | 8.3     | aarch64, ppc64le, s390x, x86\_64 | 6 months |
| RHEL          | 8.4     | aarch64, ppc64le, s390x, x86\_64 | 6 months |

---

## Usage

We provide an RPM repository for every snapshot, accessible via
`rpmrepo.osbuild.org`. The *Base URL* for a given snapshot is:

    https://rpmrepo.osbuild.org/v1/<storage>/<platform>/<snapshot>/

The parameters are:

---

| Key            | Value                   | Examples                     |
| -------------- |:-----------------------:|:----------------------------:|
| *\<storage\>*  | *anon*, *auth*, *psi*   | *anon*                       |
| *\<platform\>* | *f\<num\>*, *el\<num\>* | *f33*, *el8*                 |
| *\<snapshot\>* | *\<tag\>*               | *f33-x86\_64-devel-20201010* |

---

The *storage* key selects the actual data store. Available storage includes
*anon* for the anonymous storage, *auth* for data that requires authentication,
*psi* for data on Red Hat private infrastructure. The *platform* key groups the
data by platform, required for data lifetime management. The *snapshot* key
selects the individual snapshot.

Note that not all data is available on all storage locations and platforms. If
you select the wrong combination, you will get *404* replies. As a general
rule, you should select the platform based on the snapshot name (e.g., for the
snapshot *f33-x86\_64-devel-20201010* you should use *f33* as platform). As
storage selector, you should use *anon* for all publicly available data, *psi*
for Red Hat internal data, and *auth* if you have gotten authentication
credentials.

## Access

By default, all snapshots are publicly available, unless they contain
confidential or proprietary data. If you decide to use these snapshots, please
contact the OSBuild Developers and give us a short notice, so we can track the
users and communicate upcoming changes:

* **OSBuild Issue Tracker**: [@GitHub](https://github.com/osbuild/osbuild/issues)
* **Snapshot Maintainer**: David Rheinsberg
