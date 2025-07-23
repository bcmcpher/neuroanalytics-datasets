# Gigaconnectome

Developed by Hao-Ting Wang

The giga-connectome tool is a Brain Imaging Data Structure (BIDS)
compliant container image designed to perform post-preprocessing steps
and extract features, such as time series and connectomes, from
neuroimaging datasets that have already undergone standard
preprocessing, like that performed by fMRIPrep.

## Planned Use

The goal is to create the following standard outputs for each fMRI
session in the PREVENT-AD neuroimaging dataset.

1.  **Time Series Signals:** The tool is designed to extract time
	series signals. This extraction is implemented using nilearn
	objects, specifically `NiftiLabelsMasker` and `NiftiMapsMasker`.
	*   For time series extraction, the tool utilizes atlases
		retrieved via templateflow. Default atlases available include
		**Schaefer**, Harvard-Oxford, MIST, and DiFuMo. Notably, the
		Schaefer atlas is already used in PREVENT-AD's existing
		analytical neuroimaging pipeline for functional connectivity
		matrices.

2.  **Functional Connectomes:** The tool generates functional
	connectomes, which are matrices calculated using the extracted
	time series. These connectomes are calculated as **Pearson's
	correlation** using the nilearn object `ConnectivityMeasure`.

3.  **Post-Preprocessing Outputs:** The tool performs several critical
	post-preprocessing steps before feature extraction:
	*   **Smoothing:** Implemented with a $5 \text{mm}$ full width at
		half maximum kernel, though the user can adjust the kernel
		size.
	*   **Denoising:** The workflow is built to align closely with
		fMRIPrep's design, providing preset denoising
		strategies. Users can also implement customized strategies
		using configuration files.
	*   **Standardization:** The voxel-level data is standardized as
		z-scores.

4.  **BIDS-Connectome Format and Quality Control Reports:**
	*   The saved time series and connectomes follow the format of the
		**BIDS-connectome specification**.
	*   An **HTML visual report** is included to allow users to
		examine the quality of the atlas coverage.

The giga-connectome tool is specifically intended for large-scale
deployment on preprocessed neuroimaging datasets. The existing
PREVENT-AD cohort data includes neuroimaging analytic measures from
all MRI modalities, and specifically mentions functional connectivity
matrices obtained from resting-state fMRI outputs preprocessed using
fMRIPrep. These existing PREVENT-AD analytic measures include
connectome matrices across cortical regions of the Schaefer atlas (200
and 400 parcels) and within and between the 7 Yeo networks. The
giga-connectome tool offers a lightweight alternative aimed at
streamlining the extraction of time series and connectomes,
particularly beneficial for machine learning researchers.

## Possible Confound Corrections

The giga-connectome tool is designed to perform post-preprocessing
steps and extract features like time series and connectomes from
functional magnetic resonance imaging (fMRI) data that has already
undergone initial standard preprocessing (such as that performed by
fMRIPrep).

Before extracting the time series signals and generating functional
connectomes (calculated as Pearson's correlation), the giga-connectome
tool applies several critical steps to the voxel-level data:

1.  **Denoising (Correction for Noise/Artifacts):**
	*   The tool explicitly includes a **denoising step**.
	*   The workflow for denoising is built to align closely with the
		design choices of fMRIPrep.
	*   The implementation uses a key Application Programming
		Interface (API), `load_confounds`, from the software library
		nilearn.
	*   The tool provides **preset denoising strategies** based on
		external research (Wang et al. (2024)) and the current
		long-term support release of fMRIPrep.
	*   Users also have the option to implement **customized denoising
		strategies** using configuration files that interact directly
		with the `load_confounds` API.

2.  **Smoothing:**
	*   The tool performs **smoothing** on the voxel-level data.
	*   This is implemented using a $5 \text{mm}$ full width at half
		maximum (FWHM) kernel by default, although the user can adjust
		the kernel size based on the voxel size of their fMRI data.

3.  **Standardization:**
	*   The voxel-level data is **standardized**.
	*   This standardization is applied as **z-scores**.

These steps of smoothing, denoising, and standardization are performed
on the voxel-level data before time series signals are extracted from
the regions defined by atlases (e.g., Schaefer, Harvard-Oxford, MIST,
or DiFuMo). The extracted time series are then used to construct the
functional connectomes.

## Parcellations

The following brain parcellations (atlases) are able
to be used to build connectomes:

### I. Parcellations used by the giga-connectome tool

The **giga-connectome** tool is designed to extract time series and
generate functional connectomes using various atlases retrieved via
**templateflow**. The default atlases available in the container image
include:

*   **Schaefer**: This parcellation is specifically mentioned as a
	default atlas available in the giga-connectome tool.
*   **Harvard-Oxford**: This atlas is also listed among the default
	options available in the giga-connectome tool.
*   **MIST**: Included as a default atlas for time series extraction
	and connectome generation in giga-connectome.
*   **DiFuMo**: Listed as a default atlas available through
	templateflow and used by giga-connectome.

The tool implements time series extraction using nilearn objects,
which utilize these atlases. Users can also supply customized atlases
formatted in the templateflow convention using a configuration file.

### Parcellations used for Connectome Analysis in PREVENT-AD

The PREVENT-AD research group has previously computed
neuroimaging analytic measures, including functional connectivity
matrices, using specific parcellations:

*   **Schaefer atlas**: Functional connectivity matrices (connectome
	matrices) were obtained across cortical regions of the Schaefer
	atlas using **200** and **400 parcels** from resting-state fMRI
	data preprocessed by fMRIPrep.
*   **Yeo networks**: Connectome matrices were also obtained **within
	and between the 7 Yeo networks** (i.e., visual, sensorimotor,
	dorsal attention, ventral attention, limbic, frontoparietal, and
	default mode network).

# Reference

Wang, H. T., Gau, R., Clarke, N., Dessain, Q., & Bellec,
L. (2025). Giga Connectome: a BIDS-app for time series and functional
connectome extraction. Journal of Open Source Software, 10(110), 7061.
