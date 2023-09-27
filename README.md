# NCML to STAC

[![version](https://img.shields.io/github/v/tag/crim-ca/ncml2stac?label=latest%20version)](
https://github.com/crim-ca/ncml2stac/tree/0.0.0
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
    jupyter-repo2cwl "https://github.com/crim-ca/ncml2stac" -o .
    ```

2. Push the generated image to a Docker registry.

3. Deploy the process in Weaver.

    ```shell
    weaver deploy -u "https://example.com/weaver" -i "ncml2stac" --cwl "<generated-CWL-file>"
    ```
