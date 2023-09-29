Changes
=========

[Unreleased](https://github.com/crim-ca/ncml2stac/tree/master) (latest)
------------------------------------------------------------------------------------------------------------------

- Update STAC Item generation to transfer most NCML attribute parsing logic to `STACpopulator` implementation.
- Use changes in https://github.com/crim-ca/stac-populator/pull/23 to evaluate `STACpopulator` new conversion logic.

[0.1.0](https://github.com/crim-ca/ncml2stac/tree/0.1.0) (2023-09-29)
------------------------------------------------------------------------------------------------------------------

- Add CI utilities to test the Jupyter Notebook, build and deploy the resulting Docker image.
- Add CI configurations for tagging and defining various GitHub control flow tools.
- Remove irrelevant `Makefile` targets and add useful ones for this repository.
- Update `README` documentation with adjusted directive with real commands.
- Update `ncml2stac` notebook to display a valid STAC Item JSON as output.
- Fix Docker image generation causing `IndentError` due to `TYPE_CHECKING` directive only using `ipython2cwl` imports.

[0.0.1](https://github.com/crim-ca/ncml2stac/tree/0.0.1) (2023-09-28)
------------------------------------------------------------------------------------------------------------------

- Initial release.
