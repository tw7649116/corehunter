# R Package for Core Hunter 3

### Latest release

[![Coverage Status](http://img.shields.io/coveralls/corehunter/corehunter3-r/master.svg)](https://coveralls.io/r/corehunter/corehunter3-r)
[![Build Status](https://img.shields.io/travis/corehunter/corehunter3-r/master.svg)](https://travis-ci.org/corehunter/corehunter3-r)

### Development snapshot

[![Coverage Status](http://img.shields.io/coveralls/corehunter/corehunter3-r/develop.svg)](https://coveralls.io/r/corehunter/corehunter3-r)
[![Build Status](https://img.shields.io/travis/corehunter/corehunter3-r/develop.svg)](https://travis-ci.org/corehunter/corehunter3-r)

Core Hunter 3 is a flexible tool for multi-purpose core subset selection. Version 3 has been recoded from scratch using the [JAMES framework](http://www.jamesframework.org) which provides the applied optimization algorithms. A lot of new features have been added such as the ability to sample cores based on multiple types of genetic marker data, phenotypic traits or a precomputed distance matrix. New and improved evaluation measures were also included, that can be separately or simultaneously optimized.

Requirements
------------

A [Java Runtime Environment] (http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) (JRE) version 8 or later is required to run Core Hunter.

Getting started
---------------

The package `corehunter` can be installed from CRAN with

```R
> install.packages("corehunter")
```

Afterwards, load the package

```R
> library(corehunter)
```

and add your data, e.g.

```R
> my.genotypes <- genotypes(file = "path/to/file")
```

Sampling a core collection is then as easy as

```R
> sampleCore(my.genotypes)
```

There are numerous options when sampling a core. For example, you can change the size of the core (defaults to 20%), optimize a specific measure (defaults to average entry-to-nearest-entry distance), maximize a weighted index including multiple measures, change stop conditions (by default, the algorithm stops when it was unable to further improve the core during the last 10 seconds), etc. All functions have detailed documentation, for example try

```R
> ?sampleCore
> ?objective
> ?genotypes
> ?phenotypes
> ?distances
> ?coreHunterData
```

Many examples are included in the package as well.

Supported data types
--------------------

Core Hunter 3 supports multiple types of genetic marker data, phenotypic traits and precomputed distance matrices. See http://www.corehunter.org for more details. Data can be loaded from files, data frames and matrices.

Evaluation measures
-------------------

One of the main strengths of Core Hunter is that it can directly optimize a number of different evaluation measures. If desired, multiple measures can be simultaneously optimized as part of a weighted index. The measures included in Core Hunter 3 are listed below.

#### Distance based measures

- Average entry-to-nearest-entry distance (diversity)
- Average accession-to-nearest-entry distance (representativeness)
- Average entry-to-entry distance (provided for historical reasons, not preferred)

Gower's distance is used to compute distances from phenotypic traits, and both the Modified Roger's as well as Cavalli-Sforza & Edwards distances are supported for genetic marker data. Alternatively, a precomputed distance matrix can be used.

#### Allelic richness

- Shannon's index
- Expected heterozygosity
- Allele coverage

Available for genetic marker data only.