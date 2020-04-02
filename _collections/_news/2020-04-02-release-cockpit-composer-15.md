---
caption: "Release of cockpit-composer 15"
author: "Jacob Kozol"
---
We are happy to announce version 15 of *cockpit-composer*. Most of the work was 
spent migrating the backend from *lorax-composer* to *osbuild-composer*. There 
were also minor updates to the tests and CI.

Below you can find the official change log compiled by Jacob Kozol. Everyone is 
encouraged to upgrade!

---

## CHANGES WITH 15:

* Replace lorax-composer with osbuild-composer. This switch does not change 
  existing functionality but does enable future features.

* Update tests to increase stability and to support changes in the default 
  store.

* Remove Travis configuration which pushes to Zanata.
  
* Update NPM dependencies.

Contributions from: Jacob Kozol, Lars Karlitski, Xiaofeng Wang

-- Berlin, 2020-04-02
