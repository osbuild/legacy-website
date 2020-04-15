---
caption: "Release of osbuild-composer 10"
author: "Lars Karlitski"
categories: [fedoraplanet]
---
We are happy to announce version 10 of *osbuild-composer*, again one of our
regular biweekly releases. This release contains mostly bug fixes and internal
refactorings. We've also landed more integration tests and increased unit test
coverage.

Below you can find the official change log, compiled by Ondřej Budai. Everyone
is encouraged to upgrade!

----

* The correct metadata_expire value is now passed to dnf. In the past, this led
  to a lot of failed builds, because dnf has the default expire time set to 48
  hours, whereas the Fedora updates repos have the expire time of 6 hours.

* A decision was made that the minimal Go version required for building the
  project is 1.12. This is now enforced by the CI.

* The intermediate s3 object is now deleted after the upload to AWS is
  finished. It has no value for users.

* The upload to AWS has now a bigger timeout. The current coronavirus situation
  is affecting the AWS responsiveness in a negative way.

* The weldr API has better test coverage. In the process, several bugs in
  sources and composes were fixed.

* Worker and jobqueue packages are receiving a big refactoring.  This is the
  prerequisite for having multiple job queues for building images for different
  distributions and architectures.

* The image tests now boot the AWS images in the actual EC2.

Contributions from: Alexander Todorov, Brian C. Lane, Jacob Kozol, Jakub Rusz,
Lars Karlitski, Major Hayden, Martin Sehnoutka, Ondřej Budai, Tom Gundersen

- Liberec, 2020-04-15
