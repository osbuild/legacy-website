---
caption: "Introducing RPMrepo"
author: "David Rheinsberg"
guestpost: true
categories: [fedoraplanet]
---
The Image Builder project builds Fedora and RHEL operating system images, as
such its test infrastructure is reliant on RPM package repositories to verify
previously succeeding builds do not fail with newer Image Builder updates. It
is not unusual for CI systems to require external resources, but in the case
of RPM repositories we are suddenly confronted with a moving target: If a test
fails, was it our Image Builder modification that broke, or does the RPM
repository include broken updates?

A way to tackle this is to require all external dependencies to be immutable
and persistent. Most RPM repositories have neither of those properties, so we
as the Image Builder team introduced RPMrepo, our immutable and persistent
RPM repository snapshots.

---

# Issue Report

*Continuous Integration* tests software updates on every single change. This
ensures that problems are caught early and the need for *bisects* is reduced
significantly. For the software that is part of Image Builder, this means
test-building OS Artifacts in the CI. We want to verify that Image Builder
still correctly assembles, for example, Fedora Cloud Images, that non-standard
architecture builds still succeed, and that the different file-system types are
all still correctly compiled. This requires us to build Fedora, RHEL, and other
Operating System images from their official sources. In case of RPM based
systems, this means RPM Repositories.

It is not unusual for CI Test Suites to require external dependencies. However,
as soon as you deal with moving targets, when your dependencies are not content
addressable, or when their availability is dependent on other factors, you end
up with a test suite that can fail even though the software to be tested did
not introduce the failure. This does not necessarily mean it is not at fault,
but it significantly disrupts the following development efforts of this
project. When your test-suite starts failing without you introducing any
changes, you can no longer use it to evaluate proposed changes to your
software.

If we look at the software repositories of the Fedora project, we will face a
moving target. While the release repositories of Fedora are immutable, the
update repositories are not. They can change any time, and there is no way to
pin them at a specific point in time. This means anyone testing against those
repositories needs to be prepared with their test dependencies changing without
control.

## Immutable and Persistent Dependencies

There are different approaches to solve this problem. For Image Builder, we
decided to require all test input and dependencies to be immutable and
persistent.

#### Immutability

Immutability means that we know upfront the content that goes into our
test-suite, and thus can deduce at every step which change introduced possible
failure. We explicitly depend on a specific content hash of the RPM Repository
Metadata that is used, and thus control the data that ends up in our tests. Any
test failure thus means that this particular change caused the failure. As long
as changes come self-contained and granular, you can rely on test results to
represent a change.

This comes at a cost, though. You now need to pin the input to your test suite,
and more importantly, you need to keep it up-to-date. You thus regularly have
to update the pinned dependencies. Those updates will preferably trigger test
suite runs as well, this time telling you whether external changes caused the
failure. If those external changes cause failure, you would have to delay the
dependency update until those are resolved.

Unfortunately, this also means that all dependencies need to be persistent, so
as to retain access to the data even after the owner of that data decided to
drop it.

#### Persistency

Persistency is usually easily solved by pulling dependencies into your
project, also often known as *bundling* or *vendoring*. While it neatly avoids
any availability and persistency issues, it becomes unwieldly when the
dependencies grow in size or change regularly. With RPM repositories as
dependency, you need them to be hosted on separate infrastructure, as they can
easily surpass 50-GiB in size.

This leaves you with only one option: Mirror the required data yourself on some
central infrastructure.

## RPMrepo

After trying a lot of workarounds, mirroring subsets of repositories, avoiding
update-repositories, and other tricks, we decided that none of this worked out.
Instead, we started to create snapshots of our RPM repository dependencies, and
now control their properties ourselves. This infrastructure we called
**RPMrepo**.

**RPMrepo** has a set of input repositories, which it creates snapshots of on a
regular basis. For now, this is done on a bi-weekly schedule, but can be
amended with more snapshots at any time. The data is stored on our own
infrastructure. As those repositories can become quite big, we deploy a content
addressable shared storage system, which allows us to share any file between
snapshots in the same group. This way, we were able to significantly reduce the
required storage space of our snapshots, and we can create snapshots more often
and more regular.

These snapshots are available publicly, but we retain the option to restrict
access if this starts to exceed our budget. Furthermore, we ask everyone to
drop us a short notice if they start using the snapshots, so we can communicate
upcoming changes.

#### Using the Snapshots

For a detailed enumeration of the different parameters, check out the home of
RPMrepo. It lists the different snapshot parameters as well as the set of
repositories we currently take snapshots of.

---

**Details**: [osbuild.org/rpmrepo/]({% link _docs/rpmrepo.md %})

---

Followingly, we will walk through a short example how to access these
repositories. Lets assume you currently use the Fedora `updates-released`
repository and need a most recent snapshot. You can list all available
snapshots via:

    $ curl https://rpmrepo.osbuild.org/control/snapshots | jq .

From this list, you can pick a snapshot of your choice. If you wanted Fedora-32
on x86\_64, with the *updates-released* repository, you would possibly pick:

> f32-x86_64-updates-released-20201010

This snapshot was taken on October 10th, 2020. You now fill in the template
URL:

> `https://rpmrepo.osbuild.org/v1/<storage>/<platform>/<snapshot>/`

with your information:

> `https://rpmrepo.osbuild.org/v1/anon/f32/f32-x86_64-updates-released-20201010/`

and this will be your Base URL ready to be used with `dnf` and `yum`:

    $ curl -L https://rpmrepo.osbuild.org/v1/anon/f32/f32-x86_64-updates-released-20201010/repodata/repomd.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <repomd xmlns="http://linux.duke.edu/metadata/repo" xmlns:rpm="http://linux.duke.edu/metadata/rpm">
      <revision>1602512073</revision>
      <data type="primary">
        <checksum type="sha256">ffb5f6c80f20d9d9d972ba89bab61c564d82f65e6a1e20449056864a6787d92a</checksum>
        <open-checksum type="sha256">9891249bf4ec277851bba6349a51b8a46622ef265f4916b34c3feb6a4bfb7c68</open-checksum>
        <location href="repodata/ffb5f6c80f20d9d9d972ba89bab61c564d82f65e6a1e20449056864a6787d92a-primary.xml.gz"/>
        <timestamp>1602511955</timestamp>
        <size>5819822</size>
        <open-size>56203423</open-size>
      </data>
      [...]
    </repomd>

This is it. This snapshot is immutable and will not change during its lifetime.
Do not hesitate to contact the Image Builder team if you have questions or
further requests.
