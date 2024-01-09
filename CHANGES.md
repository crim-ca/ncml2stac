Changes
=========

[Unreleased](https://github.com/crim-ca/ncml2stac/tree/master) (latest)
------------------------------------------------------------------------------------------------------------------

<!-- list changes here, using '-' for each new entry, remove this when items are added -->

[0.3.0](https://github.com/crim-ca/ncml2stac/tree/0.3.0) (2024-01-09)
------------------------------------------------------------------------------------------------------------------

- Update STAC Item generation from NCML using `STACpopulator==0.5.0` to employ all latest fixes.

[0.2.0](https://github.com/crim-ca/ncml2stac/tree/0.2.0) (2023-10-02)
------------------------------------------------------------------------------------------------------------------

- Update STAC Item generation to transfer most NCML attribute parsing logic to `STACpopulator` implementation.
- Use changes in [crim-ca/stac-populator#23](https://github.com/crim-ca/stac-populator/pull/23) to evaluate updated
  conversion logic of `STACpopulator`.

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
