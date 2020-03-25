<img src="img/triply.png" align="right" height="150">

[![](https://img.shields.io/badge/datasets-13-brightgreen)](datasets)
[![](https://img.shields.io/badge/errors-8-red)](datasets/errors)
[![](https://img.shields.io/badge/organizations-9-orange)](organizations)

# LOD Cloud

Welcome to the Triply LOD Cloud registry!

## Get started

To use the LOD Cloud, go to https://triplydb.com and search for your
favorite Linked Dataset.

## Contribute

If your favorite Linked Dataset is not yet part of TriplyDB, you can
add its configuration in a [pull
request](https://github.com/TriplyDB/LOD-Cloud/pulls) or you can open
a ‘Dataset request’
[issue](https://github.com/TriplyDB/LOD-Cloud/issues).

## Repository structure

This registry contains records for the Linked Open Datasets that are
included in TriplyDB (https://triplydb.com) for context.

This repository is structured in the following directories:

<dl>
  <dt><code>/datasets</code></dt>
  <dd>Contains one configuration file for each Linked Open Dataset.</dd>
  <dt><code>/img</code></dt>
  <dd>Contains images that are used in dataset and organization configurations.</dd>
  <dt><code>/organizations</code></dt>
  <dd>Contains one configuration file for each organization.</dd>
  <dt><code>/rdf</code></dt>
  <dd>Contains the RDF definitions that are used by the configuration files in this repository, and includes small RDF datasets that are part of the LOD Cloud but for which we could not find an online publication elsewhere.</dd>
</dl>

## Configuration format

The files in this repository follow a specific JSON-based
configuration format.

### Dataset configuration format

The dataset configuration format is used for files in the `/datasets`
directory.

The following properties are crucial for properly connecting the
configuration files together:

  1. The value of the `image` key is the name of an image file in the
     `/img` directory.

  2. The value of the `organization` key is `"ORGANIZATION"`, which
     corresponds to the file name `ORGANIZATION.json` in the
     `/organizations` directory (see the [Organization configuration
     format](#organization-configuration-format) section below).

The following example shows the full dataset configuration for file
`datasets/owl.json`.  Notice that the value for key `image` is
`"owl.png"` and the value for key `organization` is `"w3c"`.

```json
{
  "@type": "Dataset",
  "about": [
    "Vocabulary"
  ],
  "description": "This ontology partially describes the built-in classes and properties that together form the basis of the RDF/XML syntax of OWL 2.  The content of this ontology is based on Tables 6.1 and 6.2 in Section 6.4 of the OWL 2 RDF-Based Semantics specification, available at <http://www.w3.org/TR/owl2-rdf-based-semantics/>.\n\nPlease note that those tables do not include the different annotations (labels, comments and `rdfs:isDefinedBy` links) used in this file.  Also note that the descriptions provided in this ontology do not provide a complete and correct formal description of either the syntax or the semantics of the introduced terms (please see the OWL 2 recommendations for the complete and normative specifications).\n\nFurthermore, the information provided by this ontology may be misleading if not used with care. This ontology SHOULD NOT be imported into OWL ontologies. Importing this file into an OWL 2 DL ontology will cause it to become an OWL 2 Full ontology and may have other, unexpected, consequences.",
  "exampleResource": [
    "http://www.w3.org/2002/07/owl#Axiom",
    "http://www.w3.org/2002/07/owl#Class",
    "http://www.w3.org/2002/07/owl#Thing",
    "http://www.w3.org/2002/07/owl#sameAs"
  ],
  "homepage": "https://www.w3.org/TR/owl2-overview",
  "identifier": "owl",
  "image": "owl.png",
  "license": "CC-BY-SA",
  "name": "Web Ontology Language (OWL)",
  "namespace": {
    "alias": "owl",
    "prefix": "http://www.w3.org/2002/07/owl#"
  },
  "organization": "w3c",
  "version": {
    "@type": "SemanticVersion",
    "major": 2,
    "minor": 0
  },
  "wasDerivedFrom": {
    "distribution": {
      "@type": "sdo:DataDownload",
      "contentUrl": "http://www.w3.org/2002/07/owl#"
    }
  }
}
```

### Organization configuration format

The organization configuration format is used for files in the
`/organizations` directory.

The following properties are crucial for properly connecting the
configuration files together:

  1. Each organization configuration file describes exactly one
     organization that publishes Linked Open Data.  The file name
     `ORGANIZATION.json` corresponds with the `"ORGANIZATION"` value
     of the `identifier` key.

  2. The value of the `image` key is the file name of an image in the
     `/img` directory.

The following example shows the full organization configuration file
`organizations/w3c.json`.  Notice that the value for key `identifier`
is `"w3c"`, and the value for key `image` is `"w3c.png"`.

```json
{
  "@type": "sdo:Organization",
  "description": "The World Wide Web Consortium (W3C) is an international community where Member organizations, a full-time staff, and the public work together to develop Web standards.  Led by Web inventor and Director Tim Berners-Lee and CEO Jeffrey Jaffe, W3C's mission is to lead the Web to its full potential.  Contact W3C for more information.",
  "homepage": "https://www.w3.org",
  "identifier": "w3c",
  "image": "w3c.png",
  "name": "World Wide Web Consortium (W3C)"
}
```

### Semantic definitions

The configuration files in this repository can themselves be processed
as Linked Data.  This is achieved by the following definition files:

<dl>
  <dt><code>rdf/lod-cloud.jsonld</code></dt>
  <dd>Configuration files can be processed as RDF by including the context stored in this file.</dd>
  <dt><code>rdf/lod-cloud.trig</code></dt>
  <dd>Definitions for the classes and properties that are used in the configuration files.</dd>
</dl>

## Pull request details

In order to add a new Linked Open Data to this repository, create a
[pull request](https://github.com/TriplyDB/LOD-Cloud/pulls) that
includes the following:

  - A dataset file `datasets/DATASET.json` whose contents adhere to
    the [dataset configuration format](#dataset-configuration-format).

  - An organization file `organizations/ORGANIZATION.json` whose
    contents adhere to the [organization configuration
    format](#organization-configuration-format).

  - A dataset image file and an organization image file in the `/img`
    directory.  The following image formats can be used: JPEG, PNG,
    SVG.

  - The dataset file must mention the local name of the corresponding
    organization file (see section [Configuration
    format](#configuration-format)).

  - The dataset and organization files must mention an image file in
    the `/img` directory (see section [Configuration
    format](#configuration-format)).

## Erroneous dataset

Unfortunately, many datasets cannot be included into the LOD Cloud
because they do follow standards.  Datasets that are currently not
included because of errors can be found in the
[`errors`](datasets/errors) directory.

## Missing datasets

We cannot find the datasets that correspond to the following IRI
prefixes / namespaces.  Please open a ‘Dataset request’
[issue](https://github.com/TriplyDB/LOD-Cloud/issues) if you know
where these dataset can be found.

- http://creativecommons.org/licenses/by/1.0/
- http://iandavis.com/id/
- http://purl.org/vocab/vann/
- http://vocab.org/vann/.html
- http://web.resource.org/cc/
