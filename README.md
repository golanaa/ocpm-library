# OCPM KiCad Library

Shared KiCad symbols, footprints, and frozen STEP models for OCPM-managed components.

## Contents

- `verified/`: reviewed component artifacts. Verification does not by itself mean production qualification; consult each component's metadata.
- `unverified/`: draft components and revision candidates, not approved for use as verified components.

Each directory contains a `.kicad_sym` library, a `.pretty` footprint library,
and a `.3dshapes` model directory. Component fields carry OCPM identifiers,
revision information, and engineering hashes.

## Use with Sourcerer

Keep the two checkouts beside one another:

```text
work/
├── sourcerer/
│   └── hardware/pcb/sourcerer.kicad_pro
└── ocpm-library/
    ├── verified/
    └── unverified/
```

Open Sourcerer's KiCad project. Its library tables and `OCPM_3DMODEL_DIR`
project variable already point to the sibling `ocpm-library` directory.
Use KiCad 10.0.4 or later with the standard KiCad libraries installed.

## Use in another KiCad project

Register `verified/verified.kicad_sym` and `unverified/unverified.kicad_sym`
as symbol libraries named `verified` and `unverified`. Register the corresponding
`.pretty` directories under the same footprint-library names.
Set `OCPM_3DMODEL_DIR` to this checkout's root so the footprint STEP references
resolve. Prefer project-relative library paths for collaborative projects.

## Updates

Pull this repository to obtain new library revisions. Existing placed symbols
and footprints remain embedded in a design; applying newer library revisions
is an explicit KiCad action, not an automatic consequence of pulling.

Keep drafts in `unverified`. Do not edit an approved artifact in place or change
approval fields to claim verification; submit changes through the component
review and revision workflow. This repository contains library artifacts, not
the OCPM application.
