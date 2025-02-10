# Dockerfile Bug: Inconsistent Builds due to `ubuntu:latest`

This repository demonstrates a common issue in Dockerfiles: using the `ubuntu:latest` image. This tag is not pinned to a specific version, meaning that the base image can change without warning, which may lead to inconsistent builds and runtime errors. 

## Bug

The `Dockerfile` in this repository uses the `ubuntu:latest` image, which is the source of the problem. This makes the build environment unpredictable. 

## Solution

The `Dockerfile_fixed` shows the recommended fix.  By specifying a particular Ubuntu version (e.g., `ubuntu:20.04`), we ensure consistent builds across different environments and times. The version selected is just an example and should be chosen to meet the application's dependencies and support lifecycle.

## How to reproduce

1. Clone the repository
2. Build the image using the original `Dockerfile`: `docker build -t buggy-app -f Dockerfile .`
3. Build the image using the fixed `Dockerfile`: `docker build -t fixed-app -f Dockerfile_fixed .`
4. Compare the resulting images using `docker images`. You may observe differences if you repeat the build, especially after a long period.
