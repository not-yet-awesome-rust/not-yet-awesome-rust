# Not-Yet-Awesome Rust

A curated list of Rust code and resources that do **NOT** exist yet, but would be beneficial to the Rust community.

The purpose of this list is twofold:

* Enumerate **specific use cases and their problems domains** that do not yet have a robust ecosystem in Rust.
    * The definition of "specific" and "robust" for this list is yet to be determined!
* Encourage the Rust community to approach gaps in the Rust ecosystem by providing this list as a point of collaboration!

You can jump right into editing this file [here](https://github.com/ErichDonGubler/not-yet-awesome-rust/edit/master/README.md). See the [contributing guide](CONTRIBUTING.md) for information on what you can do to help or if you have questions about this list!

## Table of contents

<!--
    To update this TOC, navigate to http://tableofcontent.eu and click "Submit" after either:
        * Pasting this Github repo's link (https://github.com/ErichDonGubler) to generate the TOC from the latest commit to `master`
        * Pasting the content of your edits into the appropriate field

    After you've generated the TOC, fluff up the output like so:

    1. Remove everything until `The List`, including the `The List` header itself.
    2. Fix the indentation to use 4 spaces instead of 2.
    3. Profit!
-->
- [Documentation](#documentation)
    - [Stack Overflow](#stack-overflow)
- [Libraries](#libraries)
    - [Character encodings](#character-encodings)
    - [Data processing](#data-processing)
    - [Data structures](#data-structures)
    - [Geometry](#geometry)
    - [Geospatial Information Systems](#geospatial-information-systems)
    - [Machine Learning](#machine-learning)
    - [Mathematics](#mathematics)
    - [Native desktop applications](#native-desktop-applications)
        - [Microsoft Office](#microsoft-office)
        - [Native UI toolkits](#native-ui-toolkits)
    - [Parsers/Emitters](#parsersemitters)
    - [Personal information management](#personal-information-management)
    - [Web bindings](#web-bindings)
        - [Google API](#google-api)
    - [XML](#xml)

## The List

### Documentation

#### Stack Overflow

* There are many older Rust questions on Stack Overflow that wouldn't work with today's Rust because of syntax that has changed since the release of 1.0, or that may have better solutions because of other Rust ecosystem developments.
    * See [#4](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/4) for an SO query and a list of these known issues!

### Libraries

#### Character encodings

* Full support for [`cp437`](https://en.wikipedia.org/wiki/Code_page_437) (see [this issue](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/21)).
    * More fully-featured encode/decode libraries like [`encoding`](https://crates.io/crates/encoding) and [`encoding-rs`](https://crates.io/crates/encoding_rs) exist, but don't support this currently.
    * A [decode-only library](https://github.com/timglabisch/rust_cp437) exists, the development of which seems to have stopped.

#### Data processing

* DDS library [wiki](https://en.wikipedia.org/wiki/Data_Distribution_Service)
* [HDF5](https://en.wikipedia.org/wiki/Hierarchical_Data_Format) (see also [Wikipedia](https://support.hdfgroup.org/HDF5/) and [this Reddit post](https://www.reddit.com/r/rust/comments/7r30r3/maintained_crate_for_hdf5_bindings/))
    * The following crates exist, but are missing some thing(s):
        * [`hdf5-rs`](https://crates.io/crates/hdf5-rs) has a lot of functionality, but is currently in design flux and has an [issue](https://github.com/aldanor/hdf5-rs/issues/17) reporting its status.
        * [`hdf5`](https://crates.io/crates/hdf5) seems capable of writing HDF5-encoded data, but not reading it.

#### Data structures

* A concurrent `HashMap`-like structure has not been fully developed yet.
    * [`concurrent-hashmap`](https://crates.io/crates/concurrent-hashmap) is still missing methods like `iter_mut`, `entry`, `drain`, and `clear` from the original `HashMap` interface.
    * [`evmap`](https://crates.io/crates/evmap) is a different design around eventual consistency, and so departs from the normal `HashMap` interface.

#### Geometry

* [PCL](http://pointclouds.org/) equivalent - point clouds, essential 3D geometry functions
* Voxel library, operations and representation of voxel data. There is [a piston crate](https://github.com/PistonDevelopers/gfx_voxel) for rendering voxels but this isn't suitable for working on domains like medical data, more geared towards game development. To enable processing in scientific domains like medicine there needs to be processing functions such as being able to: convert to triangular mesh, thresholding, and morphology. This is because things like MRI data is expressed as voxels, thresholding can separate grey and white matter in the brain, morphology identifies shapes and structures inside the body etc.

#### Geospatial Information Systems

* OGC standards - multiple crates for standards for encoding, sharing or manipulating geospatial data [link](http://www.opengeospatial.org/standards). There's already a crate for [GeoJSON](https://crates.io/crates/geojson) but none of the others appear to have crates.
* More complete GDAL wrapper (or pure rust alternative). [rust-gdal](https://github.com/georust/rust-gdal) is an incomplete wrapper so needs work.

#### Machine Learning

* Machine learning toolkit like scikit-learn in Python (both rust-learn and rusty-machine are insufficient). Rust-learn only supports classification, rusty-machines misses support for sparse data and serialization. Both of them miss quite common unsupervised techniques (like PCA).
* Deep learning toolkit with GPU support a good flexibility (think Tensorflow or Chainer in Python). Most of the current libraries are either simplistic (you cannot do seq2seq network in them for example), or miss GPU support.

#### Mathematics

* Sparse matrix libraries ([SPRS](https://github.com/vbarrielle/sprs) library needs some love, the basics are there but advanced linear algebra is missing)
* Designing low latency DSP algorithms suitable for embedded use (common filters, analysis functions)
* Library for nonlinear dynamical or chaotic systems (solvers, numeric methods etc.)

#### Native desktop applications

##### Microsoft Office

* An interactive Visual Basic uses for scripting by using the COM interface, which I believe [`winapi`](https://crates.io/crates/winapi) supports.

##### Native UI toolkits

* A mature framework for Windows native UI has yet to be established, but [`native-windows-gui`](https://crates.io/crates/native-windows-gui) claims to be approaching completion.
* Abstractions over native UI choices for each platform have yet to be available.

#### Parsers/Emitters

* ~~Ability to parse `Registry.pol` files from Windows machines~~ -- implemented [by this guy!](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/16)
* Common office document formats are yet to have more mature solutions:
    * Excel/Calc spreadsheet deserialization seems available with [`calamine`](https://crates.io/crates/calamine), but [no serialization libraries seem available](https://crates.io/search?q=office) for them, let alone for the entire XML formats that the Office/OpenOffice suites themselves support.
    * Otherwise, OpenOffice and Microsoft Office
* There is currently no library to convert between different office document formats.
* The [`beancount` data format](https://docs.google.com/document/d/1wAMVrKIA2qtRGmoVDSUBJGmYZSygUaR0uOMW1GV3YE0/edit) has no parser or emitter libraries yet.
    * A builder interface for a higher-level emission API would also be nice.
* There is no pure-Rust solution for QR decoding. The only other crate that handles QR decoding is the [`quirc`](https://crates.io/crates/quirc) crate, which uses C bindings.
* The [RData](https://www.loc.gov/preservation/digital/formats/fdd/fdd000470.shtml) file format does not have a parser or emitter yet.
    * Currently, this formatted is implemented for the R language in the [`serialize.c`](https://svn.r-project.org/R/trunk/src/main/serialize.c) module.
* There are no SGML parsers or emitters on crates.io at all.
    * This is mostly a legacy markup language used for legacy type setting and supported in applications like
	    [APP (AKA 3B2)](https://en.wikipedia.org/wiki/Arbortext_Advanced_Print_Publisher).

#### Personal information management

* Contacts via [vCard](https://en.wikipedia.org/wiki/VCard) have been implemented using [`vobject`](https://crates.io/crates/vobject), but no "high-level interface" exists yet that uses it or an alternative. <!-- FIXME: What does this actually mean? What APIs are missing/expected? -->
* [iCalendar](https://en.wikipedia.org/wiki/ICalendar) parsing has been implemented via several crates (i.e., [`vobject`](https://crates.io/crates/vobject)), but a higher-level API is missing. <!-- FIXME: What does this actually mean? What APIs are missing/expected? -->
* Bindings to the Python implementation of [`beancount`](http://furius.ca/beancount/) do not yet exist.

#### Web bindings

##### Google API

* Generation of Google bindings using [`googleapis`](https://github.com/googleapis/googleapis) and gRPC would be more performant than using JSON web requests to the Google API, as with [`google-apis-rs` service](http://byron.github.io/google-apis-rs/).
* There is room for more idiomatic APIs for Google in general. [`google-apis-rs`](http://byron.github.io/google-apis-rs/)  uses the [Google Discovery service](https://developers.google.com/discovery) to expose the vast majority of Google Services, but they can be difficult to grok for beginners or someone unfamiliar with Google APIs in general.

#### XML

There is yet to be a library that handles all of these:

* General purpose DOM tree
* Proper encoding handling
* DTD handling
    * including the disabling of features with security implications like entity expansion bombs
* XML Schema validation
* XPath
* XQuery
* XSLT 1.0/2.0/3.0
* Option to preserve input style
* Is *fast*

For more feature and performance comparisons for existing Rust XML crates, see [`choose-your-xml-rs`](https://github.com/RazrFalcon/choose-your-xml-rs).
