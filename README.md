# biomedicalDataOrganization

See the rendered document [here](https://htmlpreview.github.io/?https://github.com/stnava/biomedicalDataOrganization/blob/master/src/nrg_data_organization_summary.html)

Describe ideas regarding data organization for medical imaging and related data.

the `src` directory contains a compilable document describing the study.

the `data` directory contains example dicom data.

the `demographics` directory contains an example csv that would be paired with NRG format imaging data.

NOTE:  the csv does not match the example data in the `data` directory; the latter is just for illustration.



## Example in PPMI data

```bash

nrgdata/data/PPMI/73716
└── 20230105
    ├── DTI_LR
    │   └── 1659236
    │       ├── PPMI-73716-20230105-DTI_LR-1659236.bval
    │       ├── PPMI-73716-20230105-DTI_LR-1659236.bvec
    │       ├── PPMI-73716-20230105-DTI_LR-1659236.json
    │       └── PPMI-73716-20230105-DTI_LR-1659236.nii.gz
    ├── DTI_RL
    │   └── 1659237
    │       ├── PPMI-73716-20230105-DTI_RL-1659237.bval
    │       ├── PPMI-73716-20230105-DTI_RL-1659237.bvec
    │       ├── PPMI-73716-20230105-DTI_RL-1659237.json
    │       └── PPMI-73716-20230105-DTI_RL-1659237.nii.gz
    ├── NM2DMT
    │   ├── 1659231
    │   │   ├── PPMI-73716-20230105-NM2DMT-1659231.json
    │   │   └── PPMI-73716-20230105-NM2DMT-1659231.nii.gz
    │   ├── 1659232
    │   │   ├── PPMI-73716-20230105-NM2DMT-1659232.json
    │   │   └── PPMI-73716-20230105-NM2DMT-1659232.nii.gz
    │   ├── 1659233
    │   │   ├── PPMI-73716-20230105-NM2DMT-1659233.json
    │   │   └── PPMI-73716-20230105-NM2DMT-1659233.nii.gz
    │   ├── 1659234
    │   │   ├── PPMI-73716-20230105-NM2DMT-1659234.json
    │   │   └── PPMI-73716-20230105-NM2DMT-1659234.nii.gz
    │   └── 1659235
    │       ├── PPMI-73716-20230105-NM2DMT-1659235.json
    │       └── PPMI-73716-20230105-NM2DMT-1659235.nii.gz
    ├── T1w
    │   └── 1659228
    │       ├── PPMI-73716-20230105-T1w-1659228.json
    │       └── PPMI-73716-20230105-T1w-1659228.nii.gz
    ├── T2Flair
    │   └── 1659227
    │       ├── PPMI-73716-20230105-T2Flair-1659227.json
    │       └── PPMI-73716-20230105-T2Flair-1659227.nii.gz
    ├── rsfMRI_LR
    │   └── 1659229
    │       ├── PPMI-73716-20230105-rsfMRI_LR-1659229.json
    │       └── PPMI-73716-20230105-rsfMRI_LR-1659229.nii.gz
    └── rsfMRI_RL
        └── 1659230
            ├── PPMI-73716-20230105-rsfMRI_RL-1659230.json
            └── PPMI-73716-20230105-rsfMRI_RL-1659230.nii.gz
```

This data structure represents a hierarchical file organization for medical imaging (usually neuroimaing) data associated with the Parkinson's Progression Markers Initiative (PPMI). The tree structure for a given subject is rooted at `nrgdata/data/PPMI/73716`, indicating a specific dataset or patient ID (`73716`). Here's a breakdown of the hierarchy and the types of data it contains:

- **Root Directory**: `nrgdata/data/PPMI/73716`
  - This is the base directory for the patient or dataset with ID `73716`. All subsequent directories and files are organized under this directory.

- **Date Directory**: `20230105`
  - This directory is named after a date (`YYYYMMDD` format) indicating that the contained scans or data were collected or processed on January 5th, 2023.

- **Subdirectories**:
  - Each subdirectory represents a different type of imaging or data collection technique. Within each of these, there are further subdirectories corresponding to specific sessions, scans, or processing IDs. The files within these subdirectories contain the data and metadata for each scan or dataset.
    - **DTI_LR** and **DTI_RL**:
      - These directories contain data from Diffusion Tensor Imaging (DTI) scans, with "LR" and "RL" denoting the direction of the scanning (e.g., left-right or right-left). Each contains `.bval`, `.bvec`, `.json`, and `.nii.gz` files, which include diffusion values, vector information, metadata, and the imaging data in NIfTI format, respectively.
    - **NM2DMT**:
      - This directory is for neuromelanin.
    - **T1w** and **T2Flair**:
      - These directories contain T1-weighted and T2-FLAIR (Fluid Attenuated Inversion Recovery) MRI scans, respectively. Each has a `.json` and a `.nii.gz` file, indicating metadata and imaging data.
    - **rsfMRI_LR** and **rsfMRI_RL**:
      - These directories contain resting-state functional MRI (fMRI) data, with "LR" and "RL" again denoting scanning direction. Similar to the others, they include `.json` and `.nii.gz` files for metadata and imaging data.

This structured organization facilitates the systematic storage, access, and analysis of complex imaging data. Each file and directory is named in a way that encodes important information about the type of scan, the direction (if applicable), the patient or dataset ID, the date of acquisition, and a unique identifier for the session or scan.
