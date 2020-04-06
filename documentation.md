---
permalink: /documentation/
---
{%- include global.html -%}

# Documentation

OSBuild consists of many different projects, each serving a particular purpose.
This site tries to list all available documentation, tutorials, and resources
available for the different osbuild projects:

* [**Image Builder**](#image-builder): Product name around OSBuild, usually
  refers to the different web-interfaces for *OSBuild*.
* [**Composer**](#composer): System and API services that orchestrate image
  build requests.
* [**_osbuild_**](#osbuild): Execution engine that consumes image build
  descriptions and executes the related pipelines.

## Image Builder

_Image Builder_ is the product name around OSBuild. It consists of different
user interfaces for _OSBuild Composer_. In most cases, the documentation of the
respective user interface is the best source of help. Furthermore, the
documentation of _OSBuild Composer_ (see below) will provide insights into the
internals of the image building tools.

* **Development**: [@GitHub](https://github.com/weldr/cockpit-composer)

* **Packages**: The _Image Builder_ project is pre-packaged for the
  following distributions:

  * **Fedora**: [rpms/cockpit-composer](https://src.fedoraproject.org/rpms/cockpit-composer)

## Composer

_OSBuild Composer_ is a project providing system services to build operating
system images based on pre-defined, well-tested blueprints. The services
provide OpenAPI-compatible interfaces, as well as integration with common user
interfaces for linux systems including [Cockpit](https://cockpit-project.org).

* **Development**: [@GitHub](https://github.com/osbuild/osbuild-composer)

* **Packages**: The _OSBuild Composer_ project is pre-packaged for the
  following distributions:

  * **Fedora**: [rpms/osbuild-composer](https://src.fedoraproject.org/rpms/osbuild-composer)

## _osbuild_

The _osbuild_ project is the heart of OSBuild. It defines a pipeline
description to build arbitrary operating system images out of many small and
self-contained stages. Furthermore, it provides an execution engine that will
consume a pipeline description, execute the pipeline, and provide the resulting
image back to the user. The _osbuild_ interfaces are meant to be used by
machines, not humans. Therefore, access to _osbuild_ resources should only be
required if you plan to develop new _osbuild_ frontends, debug _osbuild_
failures on your own, or contribute to the _osbuild_ development.

* **Development**: [@GitHub](https://github.com/osbuild/osbuild)

* **Packages**: The _osbuild_ project is pre-packaged for the following
  distributions:

  * **Fedora**: [rpms/osbuild](https://src.fedoraproject.org/rpms/osbuild)
  * **Arch Linux**: [AUR/osbuild](https://aur.archlinux.org/packages/osbuild/)

* **Manual Pages**: All _osbuild_ interfaces are documented in standard Linux
  Manual Pages. They are distributed together with _osbuild_, but their latest
  version can also be accessed online:

{%- for man in global_manpages -%}
{%- assign file = man.path | split: "/" | last -%}
{% assign name = file | split: '.' | reverse | shift | reverse | join: '.' %}
  * [{{ name }}]({{ man.url | relative_url }})
{%- endfor -%}
