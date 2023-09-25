# pyFAI tutorial
This repo offers a small tutorial on pyFAI (Python fast azimuthal integration).
The tutorial is by no means complete. For full reference, please refer to the
**[official documentation](https://pyfai.readthedocs.io/en/v2023.1/)**.

The tutorial was created for the Ravnsbæk Group at Aarhus University in 
September 2023.

## Contents of the tutorial
The tutorial will take you through both calibration and azimuthal integration
of two types of x-ray scattering data: `high angular resolution powder x-ray
diffraction` data and `x-ray total scattering` data. The latter is typically 
meant for later pair distribution function (PDF) analysis.

The `pxrd` folder contains data for the tutorial on high resolution powder x-ray
diffraction data.

The `xts` folder contains data for the tutorial on x-ray total scattering data.

In both folders, `readme.md` files with instructions can be found.

## Setup and installation
### Anaconda/Miniconda
It is highly recommended to use a Python distribution through a `conda` 
package manager. If you either installed `Anaconda` (installation with a lot of
pre-installed packages) or `Miniconda` (neat installation), you are ready for further setup below. If not, `Miniconda` is recommended. Please refer to the
**[Miniconda download page](https://docs.conda.io/projects/miniconda/en/latest/index.html)**.

### Download the tutorial files
If you are familiar with `git`, you can clone the repo to get the tutorial 
files. 

Otherwise, download the contents of the repo as a `.zip` file:
- Click on the green `<> Code` button and `Download ZIP`.
- Save the `.zip` file to your local.
- Right-click on the `.zip` file and extract the files.

### Setting up conda enviroment dedicated to pyFAI
- Please open your `Anaconda Prompt`.
- Change directory to the folder containing the tutorial files. Doing this, means we will have to browse less for files later on.
```
cd /path/to/pyfai_tutorial
```
- If not already created, please create a new conda environment, dedicated to
`pyFAI`, called `pyfai_env`.  
The conda environment will contain the latest 
version of `Python 3.9` and `pyFAI`, installed from the `conda-forge` channel.  
(`pyopencl` is included here, as it is a `pyFAI` dependency, which has 
been observed to be missing, when installing `pyFAI`.)

```
conda create -n pyfai_env -c conda-forge python=3.9 pyfai pyopencl
```
- Activate your newly created enviroment.  
**NB**: This is the step to start at, whenever you are going to use your `pyfai_env` conda enviroment later on.
```
conda activate pyfai_env
```
Congratulations! You are now ready for the tutorials. Good luck!
