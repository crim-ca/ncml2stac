# NCML to STAC

[![version](https://img.shields.io/github/v/tag/crim-ca/ncml2stac?label=latest%20version)](https://github.com/crim-ca/ncml2stac/tree/0.0.1)

Converts a NCML XML with NetCDF file reference to a STAC Item JSON definition.

## CWL Application Package for Weaver OGC API - Processes

This project can be directly converted to a [Common Workflow Language (CWL)](https://www.commonwl.org/) definition
to generate a standalone and containerized *Application Package*. This package can then be deployed on
a *OGC API - Processes* capable server that supports *Part 2: Deploy, Replace, Undeploy (DRU)* extension, such
as [Weaver](https://github.com/crim-ca/weaver).

To do so, use the following steps.

1.  Generate a *CWL* corresponding to the Notebook. This will also build a Docker image with all necessary dependencies.

    ```shell
    jupyter-repo2cwl "https://github.com/crim-ca/ncml2sta" -o /tmp
    ```

    (replace the Git repository URL by the path if the clone locally)

2.  (*optional*) Push the generated Docker image to a Docker registry.

    Look for the output from the previous `jupyter-repo2cwl` command to find the generated `dockerImageId`.
    Alternatively, look for the Docker tag applied for `DockerRequirement` in `/tmp/notebooks_ncml2stac.cwl`.

    By default, the generated *CWL* will use `dockerImageId` under the `DockerRequirement`.
    This means that *CWL* will expect to run the built Docker image directly **without** pulling it.
    If the remote *Weaver* server is expected to already have the Docker image in cache
    (i.e.: `docker pull` ran manually on the server beforehand), then the tag under `dockerImageId` should be set
    by the server administrator for that pulled image on the server.

    If a different tag is used for pushing the Docker image to a Docker registry, and that it is expected that
    the *Weaver* server will automatically pull that image before running it, then the `DockerRequirement` will
    need to be adjusted accordingly with the adjusted Docker repository and image tag location.
    Specifically, the `dockerImageId` needs to be **replaced** by `dockerPull` using the selected
    registry location (e.g.: `<docker-registry>/<org>/<image:tag>`).

3.  Deploy the process in *Weaver* using the *CWL* file.

    ```shell
    weaver deploy -u http://example.com/weaver -i ncml2stac --cwl /tmp/notebooks_ncml2stac.cwl
    ```

## References

-   NCML XML to STAC Item JSON conversion logic:
    - [https://github.com/crim-ca/stac-populator](https://github.com/crim-ca/stac-populator)

-   Jupyter Notebook to CWL using `jupyter-repo2cwl`:
    - [https://github.com/common-workflow-lab/ipython2cwl](https://github.com/common-workflow-lab/ipython2cwl)
    - [https://ipython2cwl.readthedocs.io/en/latest/](https://ipython2cwl.readthedocs.io/en/latest/)

-   Git Repository to Docker with Jupyter Notebook using `jupyter-repo2docker`:
    - [https://github.com/jupyterhub/repo2docker](https://github.com/jupyterhub/repo2docker)
    - [https://repo2docker.readthedocs.io/](https://repo2docker.readthedocs.io/)
