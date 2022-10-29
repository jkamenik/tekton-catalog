# tekton-catalog

My own personal catalog of tekton tasks

## Local Development

Clone the repo `git clone git@github.com:jkamenik/tekton-catalog.git`

Open it in VSCode

```bash
cd tekton-catalog
code .
```

### Containers

Tekton tasks are containers.  All containers here are written in either go or bash.

They should be in the `./containers/<task name>/<major>.<minor>` directories

This directory should contain a Dockerfile that builds the source from that directory.  Any source or vendored libraries should be stored there as well.

The `bin/build` command can be used to build containers easily with a consistent name: `[<repo path>]<task name>:<major>.<minor>-<date>`.  For example:

1. `matrix:1.1`
2. `jkamenik/matrix:1.1`

The following `LABEL` adjust how the tags are generated:

1. `Repo` - adds a prefix (the repo path) to the container name (i.e., `gcr.io/foo/`).  Don't forget the trailing `/`.
2. `Tag` - A static tag to use as well.  Often a `-latest` or something similar `gcr.io/foo/matrix:1.1-latest`.

When in doubt use the `bin/tags` command to get a new line separated list of tags for the container.

### Tasks

Tekton tasks are yaml files that can be applied to a K8s cluster that has tekton installed.  They pair with a container that is built from the `./container` directory.