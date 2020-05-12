# Not-Yet-Awesome Rust

***An (unofficial) sub-community of the [Rust programming language](https://rust-lang.org) that wants to close gaps you feel in Rust's ecosystem.***

There are two major resources provided in this community at time of writing: [the NYAR ecosystem list](#the-list) and [issues in the NYAR tracker](#issues).

## The List

This README is a list with a twofold purpose:

* Enumerate **specific use cases and their problems domains** that do not yet have a robust ecosystem in Rust.
    * The definition of "specific" and "robust" for this list is yet to be determined!
* Encourage the Rust community to approach gaps in the Rust ecosystem by providing this list as a point of collaboration!

You can jump right into editing this file [here](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/edit/master/README.md). See the [contributing guide](CONTRIBUTING.md) for information on what you can do to help or if you have questions about this list!

## Issues

[NYAR's issue tracker](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues) can help you get ecosystem gaps filled when you participate in:

* **Voting** on your favorite issues to let people know you'd use something, optionally **commenting** and explaining your use case.
* [**Placing bounties**](https://www.bountysource.com/teams/not-yet-awesome-rust/issues) on issues you're particularly passionate about, since issues are where BountySource integrates! We use the [`bounty` tag](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues?q=is%3Aopen+is%3Aissue+label%3Abounty) to indicate which issues have bounties associated.

## Table of contents

<!--
    To update this TOC, navigate to http://tableofcontent.eu and click "Submit" after either:
        * Pasting this Github repo's link (https://github.com/not-yet-awesome-rust/not-yet-awesome-rust) to generate the TOC from the latest commit to `master`
        * Pasting the content of your edits into the appropriate field

    After you've generated the TOC, fluff up the output like so:

    1. Remove everything until `The List`, including the `The List` header itself.
    2. Fix the indentation to use 4 spaces instead of 2.
    3. Profit!
-->
- [Documentation](#documentation)
    - [Stack Overflow](#stack-overflow)
- [Libraries](#libraries)
    - ~~[Character encodings](#character-encodings)~~
    - [Computer Vision](#computer-vision)
    - [Data processing](#data-processing)
    - [Data structures](#data-structures)
    - [Dynamic programming analysis](#dynamic-programming-analysis)
    - [Embedded development](#embedded-development)
    - [Geometry](#geometry)
    - [Geospatial Information Systems](#geospatial-information-systems)
    - [Machine Learning](#machine-learning)
    - [Mathematics](#mathematics)
    - [Native desktop application integrations](#native-desktop-application-integrations)
        - [Microsoft Office](#microsoft-office)
    - [Parsers/Emitters](#parsersemitters)
    - [Personal information management](#personal-information-management)
    - [Rust Toolchain](#rust-toolchain)
    - [User Interfaces](#user-interfaces)
    - [Web bindings](#web-bindings)
        - [Google API](#google-api)
    - [XML](#xml)

## Documentation

### Stack Overflow

* There are many older Rust questions on Stack Overflow that wouldn't work with today's Rust because of syntax that has changed since the release of 1.0, or that may have better solutions because of other Rust ecosystem developments.
    * See [#4](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues/4) for an SO query and a list of these known issues!

## ~~Character encodings~~

* ~~Full support for [`cp437`](https://en.wikipedia.org/wiki/Code_page_437) (see [this issue](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues/21)).~~ Implemented [here](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues/40)!
    * ~~More fully-featured encode/decode libraries like [`encoding`](https://crates.io/crates/encoding) and [`encoding-rs`](https://crates.io/crates/encoding_rs) exist, but don't support this currently.~~
    * ~~A [decode-only library](https://github.com/timglabisch/rust_cp437) exists, the development of which seems to have stopped.~~

## Computer Vision

* Some work has been done to create OpenCV bindings in [`cv-rs`](https://github.com/nebgnahz/cv-rs) as well as automatically generating bindings like [`opencv-rust`](https://github.com/kali/opencv-rust/). Neither are very complete.
* Piston has [`imageproc`](https://github.com/PistonDevelopers/imageproc) based on [`image`](https://github.com/PistonDevelopers/image), but in their words, "This is very much a work in progress".

## Data processing

* DDS library [wiki](https://en.wikipedia.org/wiki/Data_Distribution_Service)
* ~~[HDF5](https://en.wikipedia.org/wiki/Hierarchical_Data_Format) (see also [Wikipedia](https://support.hdfgroup.org/HDF5/) and [this Reddit post](https://www.reddit.com/r/rust/comments/7r30r3/maintained_crate_for_hdf5_bindings/))~~ A stable version of [`hdf5`](https://github.com/aldanor/hdf5-rust) crate has been released and is now [available](https://crates.io/crates/hdf5) on crates.io.
* A good stream processing pipeline with back pressure doesn't yet exist for an asynchronous data processing pipeline
    * [RxRust](https://github.com/ReactiveX/RxRust) is an older attempt to implement this according to the [reactive streams](http://www.reactive-streams.org/#the-problem) model -- it currently seems closest to this use case.
    * [`tokio`](https://github.com/tokio-rs/tokio) and [`futures`](https://github.com/rust-lang-nursery/futures-rs) may be interesting components to use when building this.
    * New features soon to come in Rust like `impl Trait` will probably make developing something like this easier to develop and use.
* Bindings for [pandoc](https://pandoc.org/)
* Bindings for [git-annex](https://git-annex.branchable.com/)

## Data structures

* ~~A concurrent `std::collections::HashMap`-like structure has not been fully developed yet.~~
    * ~~[`concurrent-hashmap`](https://crates.io/crates/concurrent-hashmap) is still missing methods like `iter_mut`, `entry`, `drain`, and `clear` from the original `HashMap` interface.~~
    * ~~[`evmap`](https://crates.io/crates/evmap) is a different design around eventual consistency, and so departs from the normal `HashMap` interface.~~

    [`dashmap`](https://crates.io/crates/dashmap) is intended to fit this use case exactly.

## Dynamic programming analysis/instrumentation

* Binary instrumentation tools like [Intel Pin](https://software.intel.com/en-us/articles/pin-a-dynamic-binary-instrumentation-tool) or [DynamoRIO](http://dynamorio.org/) are useful for embedded applications. An ecosystem around them (which doesn't exist yet!) could include:
    * Bindings to the C APIs associated with existing applications (for instance, [Intel Pin](https://software.intel.com/sites/landingpage/pintool/docs/97554/Pin/html/group__API__REF.html) and [DynamioRIO](http://dynamorio.org/docs/API_BT.html))
    * Libraries or applications implementing the features of the aforementioned in Rust

## Embedded development

* [MINIX](http://www.minix3.org/) support is ~~nonexistent!~~ still a WIP.
   * [`rust-minix`](https://github.com/ids1024/rust-minix) is a WIP adding support for the Linux platform, which the author introduced with [this blog post](https://iandouglasscott.com/2019/02/18/cross-compiling-rust-code-to-minix/).

## Geometry

* [PCL](http://pointclouds.org/) equivalent - point clouds, essential 3D geometry functions
* Voxel library, operations and representation of voxel data. There is [a piston crate](https://github.com/PistonDevelopers/gfx_voxel) for rendering voxels but this isn't suitable for working on domains like medical data, more geared towards game development. To enable processing in scientific domains like medicine there needs to be processing functions such as being able to: convert to triangular mesh, thresholding, and morphology. This is because things like MRI data is expressed as voxels, thresholding can separate grey and white matter in the brain, morphology identifies shapes and structures inside the body etc.

## Geospatial Information Systems

* OGC standards - multiple crates for standards for encoding, sharing or manipulating geospatial data [link](http://www.opengeospatial.org/standards). There's already a crate for [GeoJSON](https://crates.io/crates/geojson) but none of the others appear to have crates.
* More complete GDAL wrapper (or pure rust alternative). [rust-gdal](https://github.com/georust/rust-gdal) is an incomplete wrapper so needs work.

## Machine Learning

* Machine learning toolkit like scikit-learn in Python (both rust-learn and rusty-machine are insufficient). Rust-learn only supports classification, rusty-machines misses support for sparse data and serialization. Both of them miss quite common unsupervised techniques (like PCA).
* Deep learning toolkit with GPU support a good flexibility (think Tensorflow or Chainer in Python). Most of the current libraries are either simplistic (you cannot do seq2seq network in them for example), or miss GPU support.

## Mathematics

* Sparse matrix libraries ([SPRS](https://github.com/vbarrielle/sprs) library needs some love, the basics are there but advanced linear algebra is missing)
* Designing low latency DSP algorithms suitable for embedded use (common filters, analysis functions)
* Library for nonlinear dynamical or chaotic systems (solvers, numeric methods etc.)
* A pure Rust `libm` implementation. These are required to get math functions on `#![no_std]` platforms
    * ~~The [`m`](https://crates.io/crates/m) crate has made some headway here, though it hasn't been maintained recently.~~
    * The [`libm`](https://github.com/rust-lang-nursery/libm) crate is a port of `libm` functionality from musl and newlib to Rust, with the aim of eventually being merged into `core`.

## Native desktop application integrations

### Microsoft Office

* An interactive Visual Basic uses for scripting by using the COM interface, which I believe [`winapi`](https://crates.io/crates/winapi) supports.

### Networking and Protocols

* [AMQP 1.0](https://www.amqp.org/resources/specifications) - While there are several libraries for AMQP 0.9.1, the AMQP 1.0 spec represents a significant departure from the previous version.

### Parsers/Emitters

* ~~Ability to parse `Registry.pol` files from Windows machines~~ -- implemented [by this person!](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues/16)
* Common office document formats are yet to have more mature solutions:
    * Excel/Calc spreadsheet deserialization seems available with [`calamine`](https://crates.io/crates/calamine), but [no serialization libraries seem available](https://crates.io/search?q=office) for them, let alone for the entire XML formats that the Office/OpenOffice suites themselves support.
    * Otherwise, OpenOffice and Microsoft Office
* There is currently no library to convert between different office document formats.
* The [`beancount` data format](https://docs.google.com/document/d/1wAMVrKIA2qtRGmoVDSUBJGmYZSygUaR0uOMW1GV3YE0/edit) has no parser or emitter libraries yet.
    * A builder interface for a higher-level emission API would also be nice.
    * Bindings to the [Python implementation of beancount](https://github.com/beancount/beancount) do not yet exist.
    * An [implementation of Beancount bindings, parser, and emitter in Rust](https://github.com/twilco/beancount) is currently WIP, and contributors have been requested.
* ~~There is no pure-Rust solution for QR decoding. The only other crate that handles QR decoding is the [`quirc`](https://crates.io/crates/quirc) crate, which uses C bindings~~ -- implemented [by @Wanzenbug](https://github.com/WanzenBug/rqrr) and [by @piderman](https://github.com/piderman314/bardecoder), the latter of which was announced on [Reddit](https://www.reddit.com/r/rust/comments/bk7z2x/announcing_bardecoder_a_qr_detector_and_decoder/). See [the PR](https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/pull/75).
* The [RData](https://www.loc.gov/preservation/digital/formats/fdd/fdd000470.shtml) file format does not have a parser or emitter yet.
    * Currently, this formatted is implemented for the R language in the [`serialize.c`](https://svn.r-project.org/R/trunk/src/main/serialize.c) module.
* There are no SGML parsers or emitters on crates.io at all.
    * This is mostly a legacy markup language used for legacy type setting and supported in applications like
      [APP (AKA 3B2)](https://en.wikipedia.org/wiki/Arbortext_Advanced_Print_Publisher).

### Personal information management

* Contacts via [vCard](https://en.wikipedia.org/wiki/VCard) have been implemented using [`vobject`](https://crates.io/crates/vobject), but no "high-level interface" exists yet that uses it or an alternative. <!-- FIXME: What does this actually mean? What APIs are missing/expected? -->
* [iCalendar](https://en.wikipedia.org/wiki/ICalendar) parsing has been implemented via several crates (i.e., [`vobject`](https://crates.io/crates/vobject)), but a higher-level API is missing. <!-- FIXME: What does this actually mean? What APIs are missing/expected? -->

## Rust Toolchain

* A **stable** Rust interpreter does not yet exist, which would made code exploration easier.
    * [`miri`](https://github.com/solson/miri) seems to be a step in the right direction -- it just needs some love!
* No debugging experience offers integration with `rustdoc`, which would
* A rustdoc backend for generating [zeal](https://zealdocs.org/)/
  [dash](https://kapeli.com/dash) docsets is missing.

## User Interfaces

* A mature framework for Windows native UI has yet to be established.
    * [`native-windows-gui`](https://crates.io/crates/native-windows-gui) at one point claimed to be approaching feature-completion, but is now unmaintained.
* Abstractions over native UIs for each platform have yet to be available in pure Rust.
* A good reactive UI library complete with event-driven state management comparable to [Redux](https://redux.js.org/) does not yet exist.
    * [`carboxyl`](https://github.com/aepsil0n/carboxyl) looks like it may be a good fundamental building block for this.

## Web bindings

### Google API

* Generation of Google bindings using [`googleapis`](https://github.com/googleapis/googleapis) and gRPC would be more performant than using JSON web requests to the Google API, as with [`google-apis-rs` service](http://byron.github.io/google-apis-rs/).
* There is room for more idiomatic APIs for Google in general. [`google-apis-rs`](http://byron.github.io/google-apis-rs/)  uses the [Google Discovery service](https://developers.google.com/discovery) to expose the vast majority of Google Services, but they can be difficult to grok for beginners or someone unfamiliar with Google APIs in general.

### XML

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
