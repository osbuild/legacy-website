---
caption: "Release of osbuild-composer 15"
author: "Ondřej Budai"
categories: [fedoraplanet]
---

Today, we released osbuild-composer 15 with several very exciting features.
Most notably, Composer has now support for building RHEL For Edge and also
for building images for ppc64le and s390x architectures. Also, a lot of very
nice fixes are included in this release.

Below you can find the official change log. Everyone is encouraged to
upgrade!

----

* Support for building RHEL for Edge is now available.

* Composer has now support for building QCOW2 and tar images for ppc64le and
  s390x architectures.
    
* Tar images for RHEL have returned. The Image Builder team found out that
  they are used as a way to install RHEL for Satellite.

* Blueprints containing packages with a wildcard version no longer causes
  the built image to have both x86_64 and i686 versions of one package
  installed.
  
* GPG check is now disabled by default. If you have a custom
  repository in /etc/osbuild-composer/repositories, just set gpg_check
  to true to enable the check. Note that all the pre-defined repositories
  have GPG check enabled.
    
* Composer now supports a cancellation of jobs. This can be done by calling
  /compose/cancel route of Weldr API.
   
* osbuild-composer previously crashed when osbuild didn't return the right
  machine-readable output (e.g. because of a disk being out of space). This
  is now fixed.
    
* Because of the GPG check change and RHEL for Edge support, composer
  now requires osbuild 17 or higher.
    
* osbuild-composer previously required the python package to be installed
  on RHEL. Now, it uses the always-installed platform-python.

* The buildroot for RHEL 8 didn't have selinux labels before. This is now
  fixed.
    
* When Composer crashed, it left temporary directories in /var/cache. The
  temporary directories are now moved to /var/tmp, which is managed by
  systemd with PrivateTmp set to true, so they're now correctly removed
  after a crash.
    
* Several weldr API routes were aligned to work in the same way as with
  Lorax. /blueprints/freeze now correctly supports option to output TOML.
  Projects and modules routes return all fields as Lorax returns.

* AWS upload now logs the current state to the system journal. Emojis are
  of course included. 🎉
    
* As always, amazing improvements in the CI infrastructure happened. Also,
  the test coverage went up. Thanks all for doing this!

Contributions from: Alexander Todorov, Brian C. Lane, Christian Kellner,
                    Jakub Rusz, Lars Karlitski, Major Hayden, Martin
                    Sehnoutka, Ondřej Budai, Peter Robinson, Tom
                    Gundersen

— Liberec, 2020-06-12
