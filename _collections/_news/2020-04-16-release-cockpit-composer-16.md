---
caption: "Release of cockpit-composer 16"
author: "Jacob Kozol"
categories: [fedoraplanet]
---
We are happy to announce version 16 of *cockpit-composer*, again one of our
regular biweekly releases.

This release adds the ability to upload to AWS. When creating an image 
compatible with AWS, a user has the option to upload the image to Amazon's EC2. 
This release also has minor changes to support the migration of the 
cockpit-composer repo on github to the OSBuild organization.

Below you can find the official change log, compiled by Jacob Kozol. Everyone
is encouraged to upgrade!

----

* The ability to upload to AWS has been added. The create image modal is
  replaced with a wizard enabling additional customizations and
  functionality. If the user creates an AMI the user can also enter the
  credentials and parameters needed to upload this image to EC2 in AWS.

* Cockpit-composer has migrated from Weldr to the OSBuild github
  organization. It can now be found at osbuild/cockpit-composer instead
  of weldr/cockpit-composer.

* Minor NPM updates have been made for React and Patternfly

Contributions from: Jacob Kozol

- Berlin, 2020-04-16
