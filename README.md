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


### example output data from `ANTsPyMM`

Full raw processing output in NRG format.  We usually focus on the "*wide.csv" representation of each modality.

* csv files contain tabular summary data

* png files are for reviewing image quality

* nii.gz images (scalar, tensor or vector) are derived (raw) data that provides the potential for more detailed image review and additional processing.

* trk are whole brain tractography data (large)

```bash
processedCSVSRFIRST/PPMI/73716
└── 20230105
    ├── DTI
    │   ├── 1659236
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-DTIRGB.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-DTI_norm.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-FAJHU.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-FA_norm.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-FA_norm.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-FA_norm_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-FAbetter.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-MD.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-MD_norm.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-MD_norm.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-MD_norm_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-b0avg.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-b0avg_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dti.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtifa.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtifa_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtijhulabels.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtijhulabels_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtimd.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtimd_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dtistreamlineconn.csv
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dwi.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dwi_4dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dwiavg.nii.gz
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-dwiavg_3dthumb.png
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-reoriented.bval
    │   │   ├── PPMI-73716-20230105-DTI-1659236_1659228-reoriented.bvec
    │   │   └── PPMI-73716-20230105-DTI-1659236_1659228-tractogram.trk
    │   └── 1659237
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-DTIRGB.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-DTI_norm.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-FAJHU.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-FA_norm.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-FA_norm.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-FA_norm_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-FAbetter.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-MD.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-MD_norm.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-MD_norm.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-MD_norm_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-b0avg.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-b0avg_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dti.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtifa.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtifa_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtijhulabels.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtijhulabels_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtimd.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtimd_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dtistreamlineconn.csv
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dwi.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dwi_4dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dwiavg.nii.gz
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-dwiavg_3dthumb.png
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-mmwide.csv
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-reoriented.bval
    │       ├── PPMI-73716-20230105-DTI-1659237_1659228-reoriented.bvec
    │       └── PPMI-73716-20230105-DTI-1659237_1659228-tractogram.trk
    ├── NM2DMT
    │   └── 1659235
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NM_avg.nii.gz
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NM_avg_cropped.nii.gz
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NM_labels.nii.gz
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NM_norm.nii.gz
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NM_norm_3dthumb.png
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NMavg.png
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NMavgcrop.png
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NMavgcroplabels.png
    │       ├── PPMI-73716-20230105-NM2DMT-1659235_1659228-NMavgcropt1.png
    │       └── PPMI-73716-20230105-NM2DMT-1659235_1659228-mmwide.csv
    ├── T1w
    │   └── 1659228
    │       ├── PPMI-73716-20230105-T1w-1659228-brainextraction.png
    │       ├── PPMI-73716-20230105-T1w-1659228-kk_norm.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-kk_norm.png
    │       ├── PPMI-73716-20230105-T1w-1659228-kk_norm_3dthumb.png
    │       ├── PPMI-73716-20230105-T1w-1659228-kkthickness.png
    │       ├── PPMI-73716-20230105-T1w-1659228-mmwide.csv
    │       ├── PPMI-73716-20230105-T1w-1659228-ppmi0GenericAffine.mat
    │       ├── PPMI-73716-20230105-T1w-1659228-ppmi1InverseWarp.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-ppmi1Warp.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-ppmilogjacobian.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-syn0GenericAffine.mat
    │       ├── PPMI-73716-20230105-T1w-1659228-syn1InverseWarp.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-syn1Warp.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-synjacobian.png
    │       ├── PPMI-73716-20230105-T1w-1659228-synlogjacobian.nii.gz
    │       ├── PPMI-73716-20230105-T1w-1659228-syntotemplate.png
    │       ├── PPMI-73716-20230105-T1w-1659228-thickness_image.nii.gz
    │       └── PPMI-73716-20230105-T1w-1659228-thickness_image_3dthumb.png
    ├── T1wHierarchical
    │   └── 1659228
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYN_region_reg.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYNregion_jacobian.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYNregion_reg.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYNregion_reg0GenericAffine.mat
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYNregion_reg1InverseWarp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_CIT168RRSYNregion_reg1Warp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREG_region_reg.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREGregion_jacobian.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREGregion_reg.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREGregion_reg0GenericAffine.mat
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREGregion_reg1InverseWarp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_SNREGregion_reg1Warp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-_seg.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-bf.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-bf.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brain.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brain.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brain_extraction.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brain_n4_dnz.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brainstem.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-brainstem.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-cerebellum.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-cerebellum.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-cit168.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-cit168lab.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-deep_cit168.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-deep_cit168lab.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dkt_cortex.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dkt_lobes.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dkt_parcellation.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dktcortex.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dktlobes.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-dktregions.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-hemisphere_labels.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-hemispheres.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-hippLR.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-hippLR.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-left_right.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-mmwide.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-mtl.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-mtl.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-rbp.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-snseg.csv
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-snseg.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-syn0GenericAffine.mat
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-syn1InverseWarp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-syn1Warp.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-synjacobian.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-synlogjacobian.nii.gz
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-syntotemplate.png
    │       ├── PPMI-73716-20230105-T1wHierarchical-1659228-tissue_segmentation.nii.gz
    │       └── PPMI-73716-20230105-T1wHierarchical-1659228-tissues.csv
    ├── T2Flair
    │   └── 1659227
    │       ├── PPMI-73716-20230105-T2Flair-1659227_1659228-flair.png
    │       ├── PPMI-73716-20230105-T2Flair-1659227_1659228-flairWMH.png
    │       ├── PPMI-73716-20230105-T2Flair-1659227_1659228-flairpriorWMH.png
    │       ├── PPMI-73716-20230105-T2Flair-1659227_1659228-mmwide.csv
    │       └── PPMI-73716-20230105-T2Flair-1659227_1659228-wmh.nii.gz
    └── rsfMRI
        ├── 1659229
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-CinguloopercularTaskControl.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-CinguloopercularTaskControl_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-DefaultMode.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-DefaultMode_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-DorsalAttention.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-DorsalAttention_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-FrontoparietalTaskControl.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-FrontoparietalTaskControl_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-MemoryRetrieval.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-MemoryRetrieval_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Salience.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Salience_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Subcortical.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Subcortical_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-VentralAttention.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-VentralAttention_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Visual.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-Visual_norm.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-alff.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-brain_mask.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-falff.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-meanBold.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-motion_corrected.nii.gz
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-nodescorr.csv
        │   ├── PPMI-73716-20230105-rsfMRI-1659229_1659228-rsfcorr.csv
        │   └── PPMI-73716-20230105-rsfMRI-1659229_1659228-tsnr.nii.gz
        └── 1659230
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-122-boldALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-122-boldDefaultMode.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-122-boldfALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-122-meanBOLD.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-129-boldALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-129-boldDefaultMode.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-129-boldfALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-129-meanBOLD.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-134-boldALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-134-boldDefaultMode.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-134-boldfALFF.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-134-meanBOLD.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-CinguloopercularTaskControl.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-CinguloopercularTaskControl_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-DefaultMode.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-DefaultMode_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-DorsalAttention.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-DorsalAttention_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-FrontoparietalTaskControl.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-FrontoparietalTaskControl_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-MemoryRetrieval.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-MemoryRetrieval_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Salience.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Salience_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Subcortical.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Subcortical_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-VentralAttention.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-VentralAttention_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Visual.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-Visual_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-alff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-alff_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-brain_mask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-falff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-falff_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_ContC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultMode.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DefaultMode_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DorsAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DorsAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DorsAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_DorsAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_LimbicA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_LimbicA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_LimbicB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_LimbicB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_PerAF.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_PerAF_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SalVentAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SalVentAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SalVentAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SalVentAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SomMotA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SomMotA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SomMotB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_SomMotB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_TempPar.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_TempPar_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_VisCent.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_VisCent_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_VisPeri.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_VisPeri_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_Visual.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_Visual_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_alff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_alff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_brainmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_brainmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_falff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_falff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_fmri_template.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_fmri_template_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_gmmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_gmmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_meanBold.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_meanBold_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_motion_corrected.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_motion_corrected_4dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_nodescorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_rsfcorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_tsnr.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro122_tsnr_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_ContC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultMode.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DefaultMode_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DorsAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DorsAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DorsAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_DorsAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_LimbicA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_LimbicA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_LimbicB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_LimbicB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_PerAF.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_PerAF_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SalVentAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SalVentAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SalVentAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SalVentAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SomMotA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SomMotA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SomMotB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_SomMotB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_TempPar.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_TempPar_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_VisCent.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_VisCent_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_VisPeri.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_VisPeri_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_Visual.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_Visual_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_alff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_alff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_brainmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_brainmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_falff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_falff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_fmri_template.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_fmri_template_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_gmmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_gmmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_meanBold.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_meanBold_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_motion_corrected.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_motion_corrected_4dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_nodescorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_rsfcorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_tsnr.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro129_tsnr_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_ContC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultC.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultC_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultMode.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DefaultMode_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DorsAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DorsAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DorsAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_DorsAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_LimbicA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_LimbicA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_LimbicB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_LimbicB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_PerAF.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_PerAF_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SalVentAttnA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SalVentAttnA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SalVentAttnB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SalVentAttnB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SomMotA.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SomMotA_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SomMotB.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_SomMotB_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_TempPar.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_TempPar_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_VisCent.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_VisCent_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_VisPeri.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_VisPeri_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_Visual.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_Visual_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_alff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_alff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_brainmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_brainmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_falff.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_falff_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_fmri_template.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_fmri_template_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_gmmask.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_gmmask_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_meanBold.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_meanBold_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_motion_corrected.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_motion_corrected_4dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_nodescorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_rsfcorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_tsnr.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-fcnxpro134_tsnr_3dthumb.png
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-meanBold.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-meanBold_norm.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-mmwide.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-motion_corrected.nii.gz
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-nodescorr.csv
            ├── PPMI-73716-20230105-rsfMRI-1659230_1659228-rsfcorr.csv
            └── PPMI-73716-20230105-rsfMRI-1659230_1659228-tsnr.nii.gz
```


The documented data structure represents processed / derived data from the original medical imaging datasets related to the Parkinson's Progression Markers Initiative (PPMI), specifically for the patient or dataset with ID `73716`. This structured hierarchy is located under `processedCSVSRFIRST/PPMI/73716` for the time point January 5th, 2023. Here's a detailed breakdown of the organization and content of this derivative data:

### Root Directory
- `processedCSVSRFIRST/PPMI/73716`
  - This is the base directory for processed and derivative data related to patient or dataset ID `73716`.

### Date Directory
- `20230105`
  - Indicates that the data within was processed on January 5th, 2023.

### Subdirectories and Files
Each subdirectory under the date directory represents a different type of imaging data or analysis performed on the original data. These include DTI (Diffusion Tensor Imaging), NM2DMT, T1-weighted imaging (T1w), T1w Hierarchical, T2-FLAIR, and resting-state fMRI (rsfMRI). The derivative files provide various analyses, metrics, and visualizations relevant to neuroscience and medical research. Key aspects include:

- **DTI**:
  - Contains derivative DTI data like RGB maps, template normalized versions of images, fractional anisotropy (FA) maps and metrics, mean diffusivity (MD) maps, average b0 images, tractograms, and corrected diffusion metrics. Files are organized by original DTI scan IDs (e.g., `1659236`, `1659237`) and reference specific T1w scans for anatomical context.

- **NM2DMT**:
  - Includes averaged, normalized, and labeled NM2DMT imaging data with visualizations and metrics specific to the NM2DMT scans.

- **T1w**:
  - Derivative data from T1-weighted imaging includes brain extraction visuals, normative comparisons, cortical thickness metrics, transformation matrices, and warp files indicating registration to standard templates.

- **T1w Hierarchical**:
  - Offers an extensive set of derivative data including region-specific registrations, Jacobians, segmentation visuals, anatomical labelings, cortical and lobar parcellations, and various CSV metrics detailing brain features and statistics.

- **T2Flair**:
  - Derivatives focus on FLAIR imaging with visuals of white matter hyperintensities (WMH), prior WMH estimates, and quantitative metrics of WMH volumes.

- **rsfMRI**:
  - Provides a rich set of resting-state functional connectivity metrics, ALFF/fALFF (Amplitude of Low Frequency Fluctuations/fractional ALFF) analyses, brain mask applications, motion-corrected datasets, network correlation matrices, and task-specific connectivity maps. Files are named to indicate the specific rsfMRI scan and T1w reference, with visual and quantitative derivatives for brain function and network analysis.

This structure is tailored for both basic tabular and advanced research purposes, offering a comprehensive overview of patient-specific brain structure and function through multiple imaging modalities and derived analyses. The organization facilitates easy access to specific analyses, comparisons against normative databases, and the integration of structural and functional data for in-depth study of neurological conditions.
