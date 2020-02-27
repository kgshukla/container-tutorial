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

Run the following command to inspect an image present in a remote repository. skopeo does not download the image to your local filesystem to inspect the image

      $ skopeo inspect docker://registry.access.redhat.com/rhel7
     
Check the result, see the number of layers the image has, their sha256 ids, arch_type, annotations etc

## Lab 3 - Copying OCI Images

Verify the image is not present in the local docker registry

      $ docker images | grep rhel7_orig
      
Copy the image from redhat registry

      $ skopeo copy docker://registry.access.redhat.com/rhel7 docker-daemon:registry.access.redhat.com/rhel7_orig/rhel7_orig:latest
      
Verify the image has been copied
      
      $ docker images | grep rhel7_orig
      


Run the following command to copy an image present in 
