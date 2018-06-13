This file is designed to act as a guide to handle incoming requests for model changes.

## Advantages of Versioning

- Previous changes to a data model are made comprehensible
- The current version of a data model can be compared with other versions of the data model
- It enables to reset the model to a current status
- It enables referencing
  - A varying number of applications map against the master data model. With versioning it is possible to reference against which model version the mapping was done (reference e.g. within the transformer description).

## Naming Convetion for Versioning
The name of a specific model version consists of two parts:
1. The `base name` of the data model
2. A sepcific version consting of the letter `v` and a `version number`.

The structure of the `version number` follows the standards of [SemVer - Semantic Versioning](https://semver.org/). According to SemVer a version number conists of three parts **X**, **Y** & **Z**.

The **X** stand for the _major_ version while **Y** is the _minor_ version and **Z** the _patch_ version.

According to SemVer, _major_, _minor_ and _patch_ are defined as follows:
```
Given a version number MAJOR.MINOR.PATCH, increment the:
MAJOR version when you make incompatible API changes,
MINOR version when you add functionality in a backwards-compatible manner, and
PATCH version when you make backwards-compatible bug fixes.
```

This means, every model name has the following structure:
```
<ModelName>_vX.Y.Z
```

An example for a concrete model name could look like the following:

```
OIHMasterDataModelAddresses_v1.0.0
```

Dependening on the type of model change the version number should increment in different ways. On the one hand only the number after the decimal point should increase if a minor change is made. On the other hand should the number before the decimal point be increased if a major change is made.

**Exemplary model name evolution:**

Minor change:
```
OIHMasterDataModelAddresses_v1.0.0 -> Two new nullable attributes added -> OIHMasterDataModelAddresses_v1.1.0
```
Minor change:
```
OIHMasterDataModelAddresses_v1.1.0 -> New option added to an enumaration -> OIHMasterDataModelAddresses_v1.2.0
```
Major change:
```
OIHMasterDataModelAddresses_v1.2.0 -> Type of existing attribute changed -> OIHMasterDataModelAddresses_v2.0.0
```
