# C++ build containers

This repo contains our base builder for C++ projects. The build image should contain any and all dependencies required to build our C++ projects. Also note that the Dockerfile is formatted to be optimised for image size, rather than build time. This image should not need to be rebuilt very often, so we can keep the steps and image size down to a minimum.
