# Not-Yet-Awesome Rust

A curated list of Rust code and resources that do **NOT** exist yet, but would be beneficial to the Rust community.

The purpose of this list is twofold:

* Enumerate **specific use cases and their problems domains** that do not yet have a robust ecosystem in Rust.
    * The definition of "specific" and "robust" for this list is yet to be determined!
* Encourage the Rust community to approach gaps in the Rust ecosystem by providing this list as a point of collaboration!

You can jump right into editing this file [here](https://github.com/ErichDonGubler/not-yet-awesome-rust/edit/master/README.md). See the [contributing guide](CONTRIBUTING.md) for information on what you can do to help or if you have questions about this list!

## Table of contents

<!--
    To update this TOC, navigate to http://tableofcontent.eu and paste this Github repo's link.
    After you've generated the TOC, fluff up the output like so:

    1. Remove everything until `The List`, including the `The List` header itself.
    2. Fix the indentation to use 4 spaces instead of 2.
    3. Profit!
-->
 - [Documentation](#documentation)
     - [Stack Overflow](#stack-overflow)
 - [Libraries](#libraries)
   - [XML](#xml)
   - [Data forensics](#data-forensics)
   - [Math, machine learning, data science](#math-machine-learning-data-science)


## The List

### Documentation

#### Stack Overflow

* There are many older Rust questions on Stack Overflow that wouldn't work with today's Rust because of syntax that has changed since the release of 1.0, or that may have better solutions because of other Rust ecosystem developments.
    * See [#4](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/4) for an SO query and a list of these known issues!

### Libraries

#### XML

There is yet to be a library that handles all of these:

* General purpose DOM tree
* Proper encoding handling
* DTD handling
* XML Schema validation
* XPath
* XQuery
* XSLT
* Is *fast*

For more feature and performance comparisons for existing Rust XML crates, see [`choose-your-xml-rs`](https://github.com/RazrFalcon/choose-your-xml-rs).

#### Data forensics

* ~~Ability to parse `Registry.pol` files from Windows machines~~ -- implemented [by this guy!](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/16)

#### Mathematics

* Sparse matrix libraries ([SPRS](https://github.com/vbarrielle/sprs) library needs some love, since sparse/dense matrix products are super [slow](https://github.com/vbarrielle/sprs/issues/125), otherwise is quite good)
* Designing low latency DSP algorithms suitable for embedded use (common filters, analysis functions)
* Library for nonlinear dynamical or chaotic systems (solvers, numeric methods etc.)

#### Machine Learning

* Machine learning toolkit like scikit-learn in Python (both rust-learn and rusty-machine are insufficient). Rust-learn only supports classification, rusty-machines misses support for sparse data and serialization. Both of them miss quite common unsupervised techniques (like PCA).
* Deep learning toolkit with GPU support a good flexibility (think Tensorflow or Chainer in Python). Most of the current libraries are either simplistic (you cannot do seq2seq network in them for example), or miss GPU support.

#### Data processing
* DDS library [wiki](https://en.wikipedia.org/wiki/Data_Distribution_Service)

#### Geospatial Information Systems
* OGC standards - multiple crates for standards for encoding, sharing or manipulating geospatial data [link](http://www.opengeospatial.org/standards). There's already a crate for [GeoJSON](https://crates.io/crates/geojson) but none of the others appear to have crates.
* More complete GDAL wrapper (or pure rust alternative). [rust-gdal](https://github.com/georust/rust-gdal) is an incomplete wrapper so needs work

#### Geometry
* [PCL](http://pointclouds.org/) equivalent - point clouds, essential 3D geometry functions
* Voxel library, operations and representation of voxel data. There is [a piston crate](https://github.com/PistonDevelopers/gfx_voxel) for rendering voxels but this isn't suitable for working on domains like medical data, more geared towards game development. To enable processing in scientific domains like medicine there needs to be processing functions such as being able to: convert to triangular mesh, thresholding, and morphology. This is because things like MRI data is expressed as voxels, thresholding can separate grey and white matter in the brain, morphology identifies shapes and structures inside the body etc.
