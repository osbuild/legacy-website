OSBuild Website
===============

Website Sources for the OSBuild Project

This repository contains the sources of the public website of the OSBuild
Project. It uses Jekyll to generate static content, which is immediately
deployed to serve www.osbuild.org.

### Project

 * **Website**: <https://www.osbuild.org>
 * **Bug Tracker**: <https://github.com/osbuild/osbuild.github.io/issues>

### About

The osbuild website uses static jekyll-generated sources for the website served
from https://www.osbuild.org. The website is sourced from the `main` branch
of https://github.com/osbuild/osbuild.github.io.

The website uses a collection of static pages, as well as jekyll-collections to
serve sub-pages. Currently, the landing-page is served as static overview page.
The `_news` collection provides automatically rendered blog-like entries, which
are automatically picked up under `News`.

The CI of this repository automatically builds all branches via the
`jekyll/jekyll` docker container. This does not necessarily reflect the exact
build environment that GitHub uses to generate the pages. However, it is close
enough and serves as suitable testing bed.

Furthermore, an additional workflow is set up that renders any branch that is
pushed to the repository and stores it in a subdirectory of the `preview`
branch. This means, the `preview` branch of a repository contains a rendered
version of every other branch of that respective repository, except itself.
This allows to inspect the actual website sources of PRs or experimental
branches. Additionally, if you direct GitHub to source GitHub-Pages of your
fork from the `preview` branch, you will be able to get a live preview of all
your branches (the baseurl is adjusted for all those previews to reflect the
subdirectory path).

### Requirements

The requirements for this project are:

 * `jekyll >= 4.0.0`
 * `jekyll-sitemap >= 1.4.0`

### Build

To build the website from its sources, use:

```sh
jekyll build
```

To try it out locally, use:

```sh
jekyll serve
```

Alternatively, use the `jekyll/jekyll` docker container:

```sh
docker run \
        --env "JEKYLL_UID=$(id -u)" \
        --env "JEKYLL_GID=$(id -u)" \
        --rm \
        --volume "${PWD}:/srv/jekyll" \
        "jekyll/jekyll:stable" \
        jekyll build
```

### Repository:

 - **web**:   <https://github.com/osbuild/osbuild.github.io>
 - **https**: `https://github.com/osbuild/osbuild.github.io.git`
 - **ssh**:   `git@github.com:osbuild/osbuild.github.io.git`

### License:

 - **Apache-2.0**
 - See LICENSE file for details.
