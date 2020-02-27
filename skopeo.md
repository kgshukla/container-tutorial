# Skopeo Tutorial
skopeo is a command line utility that performs various operations on container images and image repositories.

skopeo can work with OCI images as well as the original Docker v2 images.

Skopeo works with API V2 registries such as Docker registries, the Atomic registry, private registries, local directories and local OCI-layout directories. Skopeo does not require a daemon to be running to perform these operations which consist of:

    * Copying an image from and to various storage mechanisms. For example you can copy images from one registry to another, without requiring privilege.
    * Inspecting a remote image showing its properties including its layers, without requiring you to pull the image to the host.
    * Deleting an image from an image repository.
    * When required by the repository, skopeo can pass the appropriate credentials and certificates for authentication.

Skopeo operates on the following image and repository types:

    * containers-storage:docker-reference An image located in a local containers/storage image store. Location and image store specified in /etc/containers/storage.conf

    * dir:path An existing local directory path storing the manifest, layer tarballs and signatures as individual files. This is a non-standardized format, primarily useful for debugging or noninvasive container inspection.

    * docker://docker-reference An image in a registry implementing the "Docker Registry HTTP API V2". By default, uses the authorization state in $HOME/.docker/config.json, which is set e.g. using (docker login).

    * docker-archive:path[:docker-reference] An image is stored in the docker save formated file. docker-reference is only used when creating such a file, and it must not contain a digest.

    * docker-daemon:docker-reference An image docker-reference stored in the docker daemon internal storage. docker-reference must contain either a tag or a digest. Alternatively, when reading images, the format can also be docker-daemon:algo:digest (an image ID).

    * oci:path:tag An image tag in a directory compliant with "Open Container Image Layout Specification" at pa


## Getting an Environment
Click this [link](https://learn.openshift.com/subsystems/container-internals-lab-2-0-part-1) to get your lab environment. Click on "Start Session" button to begin your lab.

## Lab 2 - Inspecting OCI Images

## Lab 3 - Moving OCI Images
