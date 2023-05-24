# fixel_combat
This implements ComBat harmonisation for fixel format imaging data, based on the ComBat harmonisation for DTI data proposed by Fortin et al. (2017). This will be presented at ISMRM 2023 (Mito et al. (2023)). 

## Dependencies

### MRtrix3
To run `fixelcombat`, you will need to have a source installation of MRtrix3 available. If you do not already have this installed, navigate to the [main MRtrix3 repo](https://github.com/MRtrix3/mrtrix3), and run the following: 

```
 $ git clone https://github.com/MRtrix3/mrtrix3.git
 $ cd mrtrix3/
 $ ./configure
 $ ./build
```
*Note: `fixelcombat` requires MRtrix3 >= v3.0.0.*

### neuroCombat
`fixelcombat` also requires [neuroCombat](https://github.com/Jfortin1/neuroCombat/tree/ac82a067412078680973ddf72bd634d51deae735) to be installed. To do this run: 
```
pip install neuroCombat
```
Note that neuroCombat requires `numpy` 1.16.5 and `pandas` 1.0.3. Follow instructions on the main [neuroCombat page](https://github.com/Jfortin1/neuroCombat.git). 

### Other dependencies
This command uses `nibabel`, `pandas`, and `numpy`. Install by running:
```
$ pip install nibabel
$ pip install pandas
$ pip install numpy
```

## Installation

To install `fixelcombat`, you can clone this repository:
```
$ git clone https://github.com/remikamito/fixel_combat.git
```
Please clone this repository in the _**same location**_ as the cloned mrtrix3 repository (i.e., ~/mrtrix3 and ~/fixelcombat should be located in the same parent directory). 

### Add command to path
Once installed, you will be able to run the `fixelcombat` command using its full path (i.e., `~/fixel_combat/bin/fixelcombat`). However, you may wish to add it to your `PATH`. To do this, run the following (or add line within your `~/.bashrc` or equivalent file). 
```
$ export PATH=~/fixel_combat/bin:$PATH
```

## Usage

The basic usage for the `fixelcombat` command is:
```
fixelcombat [ options ] in_fixel_directory files design batch output_dir
``` 
- `in_fixel_directory`: the fixel directory containing input fixel data to harmonise
- `files`: a text file listing subject identifiers (one per line). This should correspond with the filenames in the fixel directory (including file extension) and be listed in the same order as the rows of the design matrix
- `design`: the design matrix (same as for `fixelcfestats`)
- `batch`: a text file corresponding to the batch (scanner variable). Rows should be listed in the same order as the subject and design matrices
- `output_dir`: the output fixel directory for ComBat harmonised fixel data. 

Options include:
- `age_index INT`: index corresponding to age column in the design matrix (if age is to be included as a biological covariate to preserve). Note that zero-indexing should be used
- `icv_index INT`: index corresponding to ICV column in the design matrix (if ICV is to be included as a biological covariate to preserve). Note that zero-indexing should be used

As with other MRtrix3 commands, you can check usage by typing in `fixelcombat` without any arguments. 

### Example usage
You may wish to perform `fixelcombat` prior to performing [`fixelcfestats`](https://mrtrix.readthedocs.io/en/latest/reference/commands/fixelcfestats.html#fixelcfestats). 

In this case you might run the following:
```
fixelcombat fdc_smooth subjects.txt design.txt batch.txt fdc_smooth_combat -age_index 2 -icv_index 3
```
In this example, we would be running `fixelcombat` on the `fdc_smooth` data, including age and ICV as biological covariates to preserve (where age is the 3rd column in design matrix, and ICV is 4th column in design matrix).

### TBC

To come:
- Specifying categorical variables for neuroCombat
- Optional arguments from neuroCombat (`eb`, `parametric`, `mean_only` and `ref_batch`).

## References

When using ComBat for the harmonisation of multi-site or -scanner fixel-based data, please cite the following:

1. JP Fortin, D Parker, B Tunc, T Watanabe, MA Elliott, K Ruparel, DR Roalf, TD Satterthwaite, RC Gur, RE Gur, RT Schultz, R Verma, RT Shinohara. Harmonization Of Multi-Site Diffusion Tensor Imaging Data. NeuroImage, 161, 149-170, 2017. [[Link here](https://www.sciencedirect.com/science/article/abs/pii/S1053811917306948?via%3Dihub#!)].
2. R Mito, H Pardoe, R Smith, J-D Tournier, D Vaughan, M Pedersen, GD Jackson. ComBat scanner harmonisation for fixel-based analysis. in Proc. Intl. Soc. Mag. Reson. Med. Toronto, Canada. p.3243, 2023 [[Link here](https://submissions.mirasmart.com/ISMRM2023/Itinerary/ConferenceMatrixEventDetail.aspx?ses=D-24)]
3. J-D Tournier, R Smith, D Raffelt, R Tabbara, T Dhollander, M Pietsch, D Christiaens, B Jeurissen, C-H Yeh, A Connelly. MRtrix3: A fast, flexible and open software framework for medical image processing and visualisation. NeuroImage, 2019, 202, 116137. [[Link here](https://www.sciencedirect.com/science/article/abs/pii/S1053811919307281)].