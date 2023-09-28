# NCML to STAC

[![version](https://img.shields.io/github/v/tag/crim-ca/ncml2stac?label=latest%20version)](
https://github.com/crim-ca/ncml2stac/tree/0.0.1
)

Converts a NCML XML with NetCDF file reference to a STAC Item JSON definition.

## CWL Application Package for Weaver OGC API - Processes

This project can be directly converted to a [Common Workflow Language (CWL)](https://www.commonwl.org/) definition
to generate a standalone and containerized *Application Package*. This package can then be deployed on 
a *OGC API - Processes* capable server that supports *Part 2: Deploy, Replace, Undeploy (DRU)* extension, such
as [Weaver](https://github.com/crim-ca/weaver).

To do so, use the following steps.

1. Generate a CWL corresponding to the Notebook. This will also build a Docker image with all necessary dependencies.

    ```shell
    jupyter-repo2cwl "https://github.com/crim-ca/ncml2sta" -o /tmp
    ```

2. Push the generated Docker image to a Docker registry.

   Look for the output from the previous `jupyter-repo2cwl` command.
   Alternatively, look for the Docker tag applied for `DockerRequirement` in `/tmp/notebooks_ncml2stac.cwl`.

   If a different tag is used for pushing the Docker image, the `DockerRequirement` will need to be adjusted
   accordingly with the adjusted Docker repository and image tag location.

3. Deploy the process in Weaver.

    ```shell
    weaver deploy -u http://example.com/weaver -i ncml2stac --cwl /tmp/notebooks_ncml2stac.cwl
    ```

## References

- Jupyter Notebook to CWL using `jupyter-repo2cwl`:
  - https://github.com/common-workflow-lab/ipython2cwl
  - https://ipython2cwl.readthedocs.io/en/latest/

- Git Repository to Docker with Jupyter Notebook using `jupyter-repo2docker`:
  - https://github.com/jupyterhub/repo2docker
  - https://repo2docker.readthedocs.io/
