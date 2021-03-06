# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [0.9.21]
### Bugs Fixed
- ```(layers/convolutional 3 0 1 64 :parents [:split-1])``` will work now.

## [0.9.20]
### Added
- Dropout is implemented in tensors (fewer cuda kernels!!)



## [0.9.19]
- pooling layer is implemented in tensors.
- Non-overlapping nms algorithm for yolo for cases where you know things cannot overlap.

## [0.9.17]
### Added
- Metrics for rating object detection systems.
- Special NMS algorithm used for yolo is now in and unit tested.


##[0.9.14]
### Added
- Yolo-style loss implemented with the tensor framework.
- Many optimizations and bugfixes around the tensor system.
- Lots of fast paths of the tensor system mapped to cudnn functions.
- Resnet50 optimizations - Memory significantly decreased (batch size of 32 possible in well under 1G video RAM).
- Resnet50 optimizations - Elide split when doing inference; simply reuse buffer without any copy operations.
- Resnet50 optimizations - GPU now pegged at 100% while training; batch upload happening during compute 100% of the time.

## [0.9.11]
### Bugs fixed
- Memory leak calling cuda kernels (!!)

## [0.9.10]
### Bugs fixed
- Small fix to ensure compilation in clojure-1.9 works properly
- Batch normalization could produce NAN in some cases.

## [0.9.9]
### Added
- "Censor" loss to prevent propagating gradients when labels are unknown
- model-upgrader project to upgrade models from older versions of cortex
- orthogonal weight initialization [#178](https://github.com/thinktopic/cortex/pull/178)
- tensorboard view [#172](https://github.com/thinktopic/cortex/pull/172)

### Changed
- Loss functions are moved to their individual files to be consistent with optimizer layout

## [0.9.8] - 2017-05-04
### Bugs fixed
- Only save base java types in file.  This avoids incompatibility issues over time and upgrades [#163](https://github.com/thinktopic/cortex/pull/163)

## [0.9.7] - 2017-05-03
### Bugs fixed
- Dependencies updated to reduce and use latest version possible of most libraries.
- thread colorspace into experiment so the mnist framework can be used for color images [#162](https://github.com/thinktopic/cortex/pull/162).


## [0.9.6] - 2017-04-28
### Bugs fixed
- inferring and training were subtly [broken](https://github.com/thinktopic/cortex/pull/161).
- Bugfixes in the classifcation [example](https://github.com/thinktopic/cortex/pull/159).


## [0.9.5] - 2017-04-26
### Added
- CPU-only support. Cortex can now run on the CPU without CUDA drivers being installed.
- docker-example -- A simple example of how to run a cortex project in a docker container.
- multi-thread -- The execution context now supports specifying the device, allowing for more advanced asynchronous computations like pipeline parallelism and using multiple devices.

### Bugs fixed
- Calling `execute/run` with a large dataset and a small batch size would throw stack-overflow exception. (https://github.com/thinktopic/think.resource/commit/0c435b2361cb5cf8f68410a9681625f7cfa7baff)
