---
title: GLEAM DP
background: /assets/home.jpeg
permalink: /
description: Data exchange format for optical radiation and visual experience data
---

**Gathered Light Exposure and Auxiliary Measurements - Data Package** (GLEAM DP) is a community-developed data exchange format for optical radiation and visual experience data. A GLEAM DP is a [Frictionless Data Package](https://specs.frictionlessdata.io/data-package/) that consists of:

File | Description
--- | ---
`datapackage.json`{:.d-inline-block style="width:150px;"} | [Metadata](metadata/) about the data package and project.
`study.json` | Metadata about the [study](metadata/#study).
`participant.json` | Metadata about the [participants](metadata/#participant) in the study.
`device.json` | Metadata about the wearable [devices](metadata/#device) used in the study.
`dataset.json` | Metadata about the [datasets](metadata/#dataset) in the study.
`placeholder-filename.csv` | Any number of files containing [data](data/) of time-stamped observations of light, visual experience, or auxiliary data.

## Context

See [visualdiet.org](https://www.visualdiet.org) to learn more about GLEAM DP and the [metadata publication](https://doi.org/10.1186/s44247-024-00113-9) to learn more about the metadata structure.

<!--
## Example

See the [example dataset](example/).
-->
## Software

- [LightLogR](https://github.com/tscnlab/LightLogR): R package to read and manipulate GLEAM DP.

## Validation

To allow validation, the `datapackage.json` of your dataset should reference the used version of GLEAM DP, both in `profile` and the resources' `schema`:

```json
{
  "name": "gleam-dataset",
  "profile": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/gleam-dp-profile.json",
  "resources": [
    {
      "name": "study",
      "path": "data/study.json",
      "profile": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/json-entity-resource.json",
      "mediatype": "application/json",
      "jsonSchema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/study.schema.json"
    },
    {
      "name": "participants",
      "path": "data/participants.json",
      "profile": "tabular-data-resource",
      "format": "json",
      "mediatype": "application/json",
      "schema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/participants.schema.json"
    },
    {
      "name": "participant_characteristics",
      "path": "data/participant_characteristics.csv",
      "profile": "tabular-data-resource",
      "format": "csv",
      "mediatype": "text/csv",
      "schema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/participant_characteristics.schema.json"
    },
    {
      "name": "datasets",
      "path": "data/datasets.json",
      "profile": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/json-entity-resource.json",
      "mediatype": "application/json",
      "jsonSchema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/dataset.schema.json"
    },
    {
      "name": "devices",
      "path": "data/devices.json",
      "profile": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/json-entity-resource.json",
      "mediatype": "application/json",
      "jsonSchema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/device.schema.json"
    },
    {
      "name": "device_datasheets",
      "path": "data/datasheets/",
      "profile": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/json-entity-resource.json",
      "mediatype": "application/json",
      "jsonSchema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/device_datasheet.schema.json"
    },
    {
      "name": "light_data",
      "path": "data/light_data.csv",
      "profile": "tabular-data-resource",
      "format": "csv",
      "mediatype": "text/csv",
      "dialect": { "delimiter": ";", "decimalChar": "." },
      "schema": "https://raw.githubusercontent.com/tscnlab/GLEAM-dp/<version>/schemas/light_data.schema.json"
    }
  ]
}
```

You can validate your dataset against the specifications of GLEAM DP (and Frictionless Data Package) with:

```shell
pip install frictionless
frictionless validate path/to/your/datapackage.json
```

## Contribute

Questions? Suggestions? Contribute to the development of GLEAM DP by watching the [repository](https://github.com/tscnlab/GLEAM-dp) and participating in [issue discussions](https://github.com/tscnlab/GLEAM-dp/issues).

## Citation

To cite the Metadata paper:

> Spitschan, M., Hammad, G., Blume, C., Schmidt, C., Skene, D., J., Wulff, K., Santhi, N., Zauner, J., Münch, M., Metadata recommendations for light logging and dosimetry datasets. BMC Digit Health 2, 73 (2024). https://doi.org/10.1186/s44247-024-00113-9

To cite the GLEAM DP standard, use the [citation provided by GitHub](https://github.com/tscnlab/GLEAM-dp), which is generated from a `CITATION.cff` file. See [About CITATION files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files) for more info.

GLEAM DP is managed by the [GLEE Team](https://www.visualdiet.org/team).

## Acknowledgement

The technical implementation of domain specific metadata to the Frictionless standard and automated documentation was supported by and is based on the the work of the [Camtrap DP](https://camtrap-dp.tdwg.org) project.
