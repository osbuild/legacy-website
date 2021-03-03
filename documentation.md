---
permalink: /documentation/
---
{%- include global.html -%}

# Documentation

OSBuild is comprised of many individual projects which
work together to provide a wide range of features to build and assemble
operating system artifacts. The graphical user interfaces can be found under
the term [**Image Builder**](#image-builder) and provide access to the osbuild
machinery. They integrate into existing operating system interfaces, including
the **Cockpit** management console, the **cloud.redhat.com** customer services,
as well as the classic linux **command-line**.

The [**Composer**](#composer) project is the underlying system service that
provides the APIs required by the multitude of user interfaces. It serves as
arbiter between the specific requirements of the user interfaces and the
general purpose functionality provided by [**osbuild**](#osbuild), the engine
that drives the builds and assemblies of the individual artifacts.

Users will find help for the graphical interfaces in the respective UI
documentation of [**Image Builder**](#image-builder). The
[**Composer**](#composer) section contains help on deploying your own build
services, or refining the blueprints of the operating system artifacts. Lastly,
information on the [**osbuild**](#osbuild) tool sheds light on the inner
workings, the system requirements, and the wide applicability of the engine and
heart of OSBuild.

## Image Builder

The **Image Builder** user interfaces integrate into existing operating system
user interfaces and extend them to support building operating system artifacts
via the OSBuild tools. These interfaces are tightly coupled with their
respective surrounding interfaces and often documented there. Followingly, a
list of external user-interfaces and links to their respective documentation,
followed by a list of user-interface documentation that is part of OSBuild
itself.

* **Cockpit Composer**: The web-based management console *Cockpit* comes
  bundled with a UI extension to build operating system artifacts. See the
  documentation of
  [**Cockpit Composer**](https://github.com/osbuild/cockpit-composer) for
  information, or consult the
  [**Cockpit Guide**](https://cockpit-project.org/guide/latest/) for help on
  general *Cockpit* questions.

* **CloudDot**: The Red Hat Customer Service Portal on *cloud.redhat.com* has
  built-in interfaces to the OSBuild functionality, allowing customers to build
  images and other artifacts on-demand. Consult the
  [**Red Hat Support Pages**](https://access.redhat.com/support) for help, or
  dive into the
  [**Image Builder Documentation**](https://github.com/osbuild/image-builder)
  to get more details on the underlying software.

* **Command-line Interface**: With **composer-cli** there exists a linux
  command-line interface (CLI) to some of the functionality provided by
  OSBuild. The CLI is part of the [**Weldr**](https://weldr.io) project, a
  precursor of OSBuild.

* **OSBuild User Documentation**:

  * [**HOWTO: Image Builder + OSTree + Anaconda**]({% link _news/2020-06-01-how-to-ostree-anaconda.md %})

## Composer

The system service **OSBuild Composer** provides APIs and services to build
operating system images and other artifacts. It defines the blueprints of a
wide range of images and a managed environment to execute the required build
pipelines.

The **Composer** service exports a large set of APIs, each tailored for a
specific user-interface and use-case. Underneath, it converts all API requests
to a uniform worker API which uses the **osbuild** machinery to execute the
build pipelines.

For high-level documentation and information on development, see its
[Project Pages @GitHub](https://github.com/osbuild/osbuild-composer).

* **OSBuild Composer Administrator Documentation**:

  * [osbuild.org/guides](https://www.osbuild.org/guides/)

## _osbuild_

The _osbuild_ project is the heart of OSBuild. It defines a pipeline
description to build arbitrary operating system artifacts out of many small and
self-contained stages. Furthermore, it provides an execution engine that will
consume a pipeline description, execute the pipeline, and provide the resulting
image back to the user. The _osbuild_ interfaces are meant to be used by
machines, not humans. Therefore, access to _osbuild_ resources should only be
required if you plan to develop new _osbuild_ frontends, debug _osbuild_
failures on your own, or contribute to the _osbuild_ development.

For high-level documentation and information on development, see its
[Project Pages @GitHub](https://github.com/osbuild/osbuild).

* **OSBuild System Documentation**:

{% for man in global_manpages -%}
{%- assign file = man.path | split: "/" | last -%}
{% assign name = file | split: '.' | reverse | shift | reverse | join: '.' %}
  * [**MAN: {{ name }}**]({{ man.url | relative_url }})
{%- endfor %}

* **OSBuild Developer Documentation**:

  * [**Introducing RPMrepo**]({% link _news/2020-10-23-introducing-rpmrepo.md %})
  * [**RPMrepo: RPM Repository Snapshots**]({% link _docs/rpmrepo.md %})
