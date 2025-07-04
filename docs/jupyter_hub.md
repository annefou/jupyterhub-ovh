# Deploy JupyterHub on OVH 

## Overview

### Features

- **Interactive Data Analysis**: Utilize Jupyter notebooks for dynamic data exploration and modeling.
- **Robust Computational Resources**: Leverage cloud capabilities for large-scale computations.
- **Integration with Data**: Access and analyze datasets from different sources.

## Setup and administration

This section provides an overview of where to find information and source code related to the deployment and administration of OVH JupyterHub.
It also explains how and by whom users can be added.

### JupyterHub deployment on OVH

The source code and documentation to deploy the JupyterHub on OVH are available in the `gfts-track-reconstruction` folder, located in the root directory.

A good starting point is the [README.md](https://github.com/annefou/jupyterhub-ovh/blob/main/gfts-track-reconstruction/jupyterhub/README.md) file, located in the `gfts-track-reconstruction/jupyterhub` folder.

#### JupyterHub User Image

The user image is defined in the [gfts-track-reconstruction/jupyterhub/images/user](https://github.com/annefou/jupyterhub-ovh/tree/main/gfts-track-reconstruction/jupyterhub/images/user) folder and consists of:

- [Dockerfile](https://raw.githubusercontent.com/annefou/jupyterhub-ovh/main/gfts-track-reconstruction/jupyterhub/images/user/Dockerfile) where you can review the Pangeo base image we are using, and see how additional conda and pip packages are installed, among other details;
- [conda-requirements.txt](https://github.com/annefou/jupyterhub-ovh/blob/main/gfts-track-reconstruction/jupyterhub/images/user/conda-requirements.txt) contains the list of packages to be installed with conda. To suggest the installation of a new conda package, you can edit this file and make a Pull Request. Be sure to follow the `requirements.txt` format when adding new packages.
- [requirements.txt](https://github.com/annefou/jupyterhub-ovh/blob/main/gfts-track-reconstruction/jupyterhub/images/user/requirements.txt) contains the list of packages installed with pip. Similarly, you can suggest adding new pip packages by editing this file and submitting a Pull Request.

### S3 Buckets

Limited storage is available on the Jupyterhub itself but we have setup different S3 buckets where we manage the data we need for the project. We currently have different S3 buckets which we can split into 2 categories:

1. Public S3 buckets: these buckets enable to share data to all users of the platform.
   - "**gfts-reference-data**": This S3 bucket contains reference datasets (such as Copernicus Marine) that have been copied here to speed up access and data processing. Most users will only require read-only access to this bucket; a few users can write to it to copy new reference datasets. If you need additional reference datasets, please create an issue [here](https://github.com/annefou/jupyterhub-ovh/issues/new).
   - "**destine-gfts-data-lake**": This S3 bucket contains datasets generated by the JupyterHub, which are intended to be made public for all users with access to the Jupyterhub;
2. Private S3 buckets: these buckets contain datasets that are private to a specific group. All users of a given group have **read** and **write** access to their corresponding buckets. Users can store private datasets or save intermediate results that will be shared in **destine-gfts-data-lake** once validated.
   - "**gfts-ifremer**": This S3 bucket contains datasets that are private to IFREMER JupyterHub users.
   - "**gfts-vliz**": This S3 bucket contains datasets that are private to VLIZ Jupyterhub users.

### Admin Hub

- **User Management**: Administrators can add new users to the JupyterHub, granting access to computational resources and data sets.
- **Deployment Configuration**: Details on configuring the JupyterHub environment, including Docker image setups and package installations.
- **Data Access Control**: Instructions for managing permissions to S3 buckets and other data resources.

:::{seealso}

For detailed instructions on adding new users, please refer to [Admin Hub Documentation](admin_hub.md).

:::
