---
caption: "Release of osbuild-composer 16"
author: "Ondřej Budai"
categories: [fedoraplanet]
---

We are happy to announce that we released osbuild-composer 16 yesterday.
This release has no new features but contains a lot of useful fixes.

Below you can find the official change log. Everyone is encouraged to
upgrade!

----

* osbuild-composer now obsoletes lorax-composer on RHEL.

* An upload failure (e.g. due to invalid credentials) now causes the compose
  to appear as failed.
    
* RHEL 8 repositories are switched to the beta ones to allow composer to be
  tested on 8.3 Beta. This will be reverted when GA comes.
  
* OSTree images no longer contains /etc/fstab. The filesystem layout is
  determined by the installer and thus it doesn't make any sense to include
  it.
    
* If both group and user customizations were used, the user would be created
  before the group, causing a build to fail. This is now fixed.
    
* Composer now correctly passes UID and GID to org.osbuild.{users,groups}
  stages as ints instead of strings.

* The subpackages (worker, tests and rcm) now require a matching version of
  osbuild-composer to be installed. Previously, they would be happy with
  just an arbitrary one.

* Support for testing OpenStack images in actual OpenStack is now available.
  Note that upload to OpenStack is still not available for the end users
  (it's on the roadmap though).
    
* Worker now logs not only job failures but also job successes.
  
* All DNF errors were mistakenly tagged as RepoError, this is now fixed.
  
* As always, a lot of test and CI improvements are included in this release.

Contributions from: Alexander Todorov, Christian Kellner, Major Hayden, Martin
                    Sehnoutka, Ondřej Budai, Tom Gundersen

— Liberec, 2020-06-29
