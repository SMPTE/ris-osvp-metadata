<!---
// SPDX-License-Identifier: CC-BY-4.0
// Copyright Contributors to the SMTPE RIS OSVP Metadata Project
-->

# SMPTE RIS OSVP Metadata Project

DRAFT - April 12, 2023

This repository hosts the metadata work of the SMPTE Rapid Industry Solutions program for On-Set Virtual Production (RIS OSVP) where SMPTE has brought together a group of experts to advance education and technology for OSVP.

This material in this repository is intended to improve the understanding and interoperability of metadata in On-Set Virtual Production and possibly serve as the basis for standards, specifications and additional open source projects. The repository will eventually encompass camera, lens, and tracking metadata both for traditional VFX and for ICVFX. Currently, the repository hosts the initial work output, which is focused on camera and lens metadata for VFX as traditionally carried out in post. Additonal work is underway on tracking and ICVFX.

The principal metadata work of the group consists of [tables of camera and lens metadata for VFX](vfx/camera-lens-tables.md).

The work also includes CAMDKIT (https://github.com/SMPTE/ris-osvp-metadata-camdkit), a Python codebase that can ingest the outputs from various camera maker's tools and output them in a normalized JSON format defined by CAMDKIT. When parameter names are defined in SMPTE ST 2065-4:2013 ACES Image Container File Layout, CAMDKIT's JSON uses those, with the names in the [tables](vfx/camera-lens-tables.md) being the corresponding more human readable (space-separated) versions.

The repository also lists a set of [reference materials](references/camera-lens-references.md) related to camera and lens metadata for VFX and ICVFX.

## LICENSE

The SMPTE RIS OSVP Metadata project publications are open source. Please see the [LICENSE](LICENSE.md) file in each repository for details.

## CONTACT

If you have comments or questions, you can send email to ris-osvp-metadata@smpte.org or open an issue on GitHub.

<sub>Licensed under a Creative Commons Attribution 4.0 license<br></sub>
