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

### nibabel
This command uses `nibabel`. Install by running:
```
$ pip install nibabel
```

## Installation

To install `fixelcombat`, you can clone this repository:
```
$ git clone https://github.com/remikamito/fixel_combat.git
$ cd fixel_combat/
$ ./build
```
For the `build` command to work, it needs to invoke the main MRtrix3 `build` script. Please clone this repository in the _**same location**_ as the cloned mrtrix3 repository (i.e., ~/mrtrix3 and ~/fixelcombat should be located in the same parent directory). 

## Usage



## References

When using ComBat for the harmonisation of multi-site or -scanner fixel-based data, please cite the following:

1. JP Fortin, D Parker, B Tunc, T Watanabe, MA Elliott, K Ruparel, DR Roalf, TD Satterthwaite, RC Gur, RE Gur, RT Schultz, R Verma, RT Shinohara. Harmonization Of Multi-Site Diffusion Tensor Imaging Data. NeuroImage, 161, 149-170, 2017. [[Link here](https://www.sciencedirect.com/science/article/abs/pii/S1053811917306948?via%3Dihub#!)].
2. R Mito, H Pardoe, R Smith,J-D Tournier, D Vaughan, M Pedersen, GD Jackson. ComBat scanner harmonisation for fixel-based analysis. in Proc. Intl. Soc. Mag. Reson. Med. Toronto, Canada. p.3243, 2023 [[Link here](https://submissions.mirasmart.com/ISMRM2023/Itinerary/ConferenceMatrixEventDetail.aspx?ses=D-24)]
