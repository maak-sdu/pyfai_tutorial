# High resolution powder x-ray diffraction
## Experimental details
Beamline: P02.1, PETRA III, DESY.  
Wavelength: 0.207332 Å  
Sample-to-detector distance (approx.): 1200 mm  
Polarization factor: 0.9

## Prerequisites
It is assumed that you already created a `pyfai_env` conda environment dedicated
to pyFAI and have this activated.  
It is also assumed that you downloaded to the tutorial files and navigated to 
the `pyfai_tutorial` directory on your local.

## Calibration
For calibration, we are going to call the `pyfai-calib2` graphical user 
interface (GUI).
```
pyfai-calib2
```
If you are familiar with other software for azimuthal integration, e.g., Fit2D, 
DAWN, etc., it should be rather intuitive to go through the various steps below.  

### Experimental settings
- Insert the wavelength stated in the top of this file.  
- Choose the calibrant ($\mathrm{LaB_{6}}$ or $\mathrm{CeO_{2}}$) that you are going to use.
- Load the image file.
- Regarding the detector, pyFAI comes with some pre-installed detectors.  
Unfortunately, for our case, we will need to state detector information 
manually.  
From the size (pixels x pixels) stated for the image file that you loaded, 
you'll be able to state the detector size (pixels x pixels).  
However, for the pixel size, try to go to 
[the unified datasheet](https://photon-science.desy.de/facilities/petra_iii/beamlines/p021_powder_diffraction_and_total_scattering_beamline/unified_data_sheet/index_eng.html)
for the beamline.  
Then, you should be able to get the information needed for the pixel size.
- Click `Next >`.

### Mask
- Mask beamstop, e.g., using the ring tool.
- Mask beamstop arm, e.g., using the box or polygon tools.
- Mask dead pixels (`Mask Below` values of zero).
- Mask overexposed pixels (`Mask not finite values`).
- Save your mask (your mask can be saved in various file formats, e.g., `.npy`.
- Click `Next >`.

### Peak picking
- Pick rings. (Start with the innermost.)
- Keep an eye on whether some rings are missed, merged, etc., and adjust the
enumeration, unpick, re-pick, etc.
- Save the picked rings for possible later inspection. (`.npt` file)
- Click `Next >`.

### Geometry fitting
- Check whether the wavelength stated is correct.
- Check whether the refined values look reasonable.
- If not, go back to the `Peak picking` step before and inspect your picks, 
enumeration, etc.
- If reasonable, click `Next >`.

### Caking and integration
- Choose the radial unit that you expect to integrate to later, e.g., $Q$ in 
$\mathrm{\AA}^{-1}$ or $2\theta$ in $\degree$.  
(Just for visual inspection.)
- Set the number of `Radial points` to `2000`.
- Use `360` for `Azimuthal points`.
- Activate the `Polarization factor` and use the value stated in the top of this
file.  
(**NB**: The value is beamline-dependent.)
- Click on `Integrate`.
- Click on `Save as PONI file`. (**P**oint **O**f **N**ormal **I**ncidence.)
- Close the GUI window.

## Integration
For the azimuthal integration, we are going to call the `pyfai-integrate` gui.
```
pyfai-integrate
```
- To import info on the experimental geometry, click on `Import from file...` 
and choose the `.poni` saved from the calibration step.
- Check whether the loaded values look reasonable.
- Activate and load the `Mask file` that you created during the calibration.
- Activate and set the polarization factor used during the calibration.
- Set the `Radial unit`, e.g., $Q$ in $\mathrm{\AA}^{-1}$ or $2\theta$ in
$\degree$.
- Set the `Number of points` to `2000`.
- If desired, choose `Error propagation` choose your preferred method.
- If desired, choose normalization.
- If desired, choose a pixel splitting method under `Algorithm`.
- Save your azimuthal integration configuration to a `.json` file by clicking 
`Save config...`.
- Conduct the azimuthal integration by clicking `Batch processing...` and choose the file(s) (within a single directory) to process.
- The azimuthally integrated data are saved to `.dat` file(s) within the 
directory of the processed (`.tif`) file(s).
- Inspect the azimuthally integrated data by plotting the `.dat` file(s).

This concludes the tutorial reagarding high resolution powder x-ray diffraction data. If relevant, consider trying the workflow presented here for *operando* 
data.
