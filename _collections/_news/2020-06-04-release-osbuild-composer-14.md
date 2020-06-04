---
caption: "Release of osbuild-composer 14"
author: "Ondřej Budai"
categories: [fedoraplanet]
---

Osbuild-composer 13 had numerous new exciting features but unfortunately,
several annoying bugs slipped into that release too. To address all these
issues, yesterday our team decided to roll-out an off-schedule bug-fix
release. Say hi to osbuild-composer 14.

The most important news is: AWS upload support got several fixes making it
more stable and the internal store can now handle manifests with a no longer
supported schema. Also, we dropped support for i686 architecture. Building
images for it was never supported and we now no longer provide i686 RPMs.

See the full changelog below.

----

* AWS uploads doesn't anymore report to AWS that composer uploads
  the image in vhdx format. This surprisingly makes the upload process
  more stable.

* Uploads were always in WAITING state. This is now fixed.
  
* The /projects/source/* routes now correctly supports all the features
  of Weldr API v1. 

* AWS upload now logs the progress to journal. Even better logging is
  hopefully coming soon.
    
* AWS upload's status is now correctly set to FAILED when ImportSnapshot
  fails. Before, this hanged the upload indefinitely.

* Store unmarshalling is now safer in some cases. For example, stored
  manifests are now longer checked when loaded from disk. Therefore,
  changing of manifest schema doesn't lead to crashes when old manifests
  are present in the store.
  
* When store loading failed in non-verbose mode of osbuild-composer, it
  crashed the process because of nil logger. This is now fixed.

* The upstream spec file for building osbuild-composer package now
  excludes the i686 architecture. Note that composer never supported
  this arch.
    
* The upstream spec file now correctly specifies the composer's dependency
  to osbuild-ostree. This was forgotten in the previous release which
  introduced Fedora IoT support.

* The previous version didn't have repositories defined for s390x and
  ppc64le architectures. This is now fixed. Note that this only fixes
  some codepaths, osbuild-composer still cannot build any images on
  these architectures. 

Contributions from: Brian C. Lane, Lars Karlitski, Major Hayden, Martin
                    Sehnoutka, Ondřej Budai, Stef Walter, Tom Gundersen

— Liberec, 2020-06-03
