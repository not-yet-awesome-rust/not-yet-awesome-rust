# Not-Yet-Awesome Rust

A curated list of Rust code and resources that do **NOT** exist yet, but would be beneficial to the Rust community.

The purpose of this list is twofold:

* Enumerate **specific use cases and their problems domains** that do not yet have a robust ecosystem in Rust.
    * The definition of "specific" and "robust" for this list is yet to be determined!
* Encourage the Rust community to approach gaps in the Rust ecosystem by providing this list as a point of collaboration!

See the [contributing guide](CONTRIBUTING.md) for information on what you can do to help or if you have questions about this list!

## Table of contents

***TODO***

## The List

### Documentation

### Stack Overflow

* There are many older Rust questions on Stack Overflow that wouldn't work with today's Rust because of syntax that has changed since the release of 1.0, or that may have better solutions because of other Rust ecosystem developments.
    * See [#4](https://github.com/ErichDonGubler/not-yet-awesome-rust/issues/4) for an SO query and a list of these known issues!

### Libraries

#### Data forensics

* Ability to parse `Registry.pol` files from Windows machines

#### Math, machine learning, data science

* Sparse matrix libraries ([SPRS](https://github.com/vbarrielle/sprs) library needs some love, since sparse/dense matrix products are super [slow](https://github.com/vbarrielle/sprs/issues/125), otherwise is quite good)
* Machine learning toolkit like scikit-learn in Python (both rust-learn and rusty-machine are insufficient). Rust-learn only supports classification, rusty-machines misses support for sparse data and serialization. Both of them miss quite common unsupervised techniques (like PCA).
* Deep learning toolkit with GPU support a good flexibility (think Tensorflow or Chainer in Python). Most of the current libraries are either simplistic (you cannot do seq2seq network in them for example), or miss GPU support.
