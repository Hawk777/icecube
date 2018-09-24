Introduction
============

Icecube’s purpose is to interact with Amazon Glacier, a long-term data archival
service. Data in Amazon Glacier is stored in a two-level hierarchy. First, one
creates *vaults*, equivalent to directories. Each vault has a user-specified
name. Second, one creates *archives* within the vaults, each of which is
equivalent to a single file. Each archive has an optional user-specified
description.

The list of available vaults can be retrieved at any time. The list of archives
in a vault is recorded in an *inventory*. Inventories are not updated
immediately, and furthermore obtaining an inventory constitutes a retrieval job
with a multi-hour latency. Thus, it is preferable to keep a local record of
mappings between archive IDs and human-readable names. It may be appropriate to
download a vault inventory from time to time to ensure the mapping is correct.

Features
========

Icecube supports the following operations:

* Listing, creating, and deleting vaults
* Adding archives to vaults
* Uploading large archives using multipart uploads so retries are possible (multipart mode is selected automatically when appropriate)
* Reading an archive to upload from a pipe or standard input (including very large archives—the complete archive is never stored)
* Deleting archives from vaults
* Starting jobs to download archives or vault inventories
* Checking the status of jobs on a vault
* Downloading the outputs of jobs (both archives and inventories)

The following features are available from Glacier but are not currently supported by Icecube:

* Configuring vault notifications (this can be done through the AWS web console, and notifications thus configured are respected)
* Setting a custom notification method for a single job (all jobs use the notification settings for the vault)
* Resuming an archive upload after the program has been terminated

Usage
=====

Usage information is available by running `icecube` with no command-line parameters.

License
=======

Icecube is © Christopher Head and is released under the GNU General Public
License version 3.
