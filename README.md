# Segmentation of selected solar corona structures
## Systems and user manual
---

### Author: Bc. Ľubomír Lazor
### Supervisor: doc. Ing. Martin Sarnovský, PhD.
Department of Cybernetics and Artificial Intelligence, Faculty of Electrical Engineering and Informatics, Technical University of Košice, Košice, Slovakia


## Abstract
This thesis explores the use of deep learning for the automated segmentation of coronal holes (CHs) and active regions (ARs) in solar EUV images. These structures are key to understanding solar activity and predicting space weather. Building on the SCSS-Net model, a U-Net-based architecture, this work combines theoretical insights with practical modeling to assess performance of various configurations. The results show that deep learning can offer a reliable, scalable solution for the segmentation of solar structures driven by thoughtful data handling and model design.

---

# File structure
The file structure expands on the already existing [SCSS-Net](https://github.com/space-lab-sk/scss-net). The new additions are two models (one for the segmentation of coronal holes and one for the segmentation of active regions), two datasets, 4 jupyter notebook with code and a textfile with requirements.

```text
├── 📁 scss-net/
│   ├── 📁 src/
│   │   ├── metrics.py
│   │   ├── model_scss_net.py
│   │   ├── prep_utils.py
│   │   └── utils.py
│   ├── 📁 models/
│   │   ├── ar_model.h5
│   │   └── ch_model.h5
│   ├── 📁 data/
│   │   ├── 📁 AR
│   │   │   ├── 📁 images_renamed
│   │   │   └── 📁 masks_renamed
│   │   └── 📁 CH
│   │   │   ├── 📁 images_renamed
│   │   │   └── 📁 masks_renamed
│   ├── 📁 Reiss_dataset/
│   │   ├── 📁 images
│   │   └── 📁 masks
│   ├── requirements.txt
│   ├── U-net_AR_evaluation_only.ipynb
│   ├── U-net_AR.ipynb
│   ├── U-net_CH_evaluation_only.ipynb
│   └── U-net_CH.ipynb
├── Solar_corona_structures_detection_and_segmentation.pdf #article
└── README.md        
```

# Datasets

* First dataset consists of EUV images from SDO/AIA and SUVI/GOES instruments, namely the channels 193 Å and 191 Å for coronal holes and 171 Å for active regions, and SPoCA masks for both active regions and coronal holes. Due to storage constraints, the data was not able to fit inside the appendices. Test data is available at this [link](https://mega.nz/file/rZVVlLKK#pSP0Rz9Z_ZgxibT-078qUDhOg_yNEmdPyqdnXFvvpuc) (~1.9 GB), training and validation data can be provided upon request.

* The second dataset introduced by [Reiss et al. (2024)](https://figshare.com/articles/dataset/Coronal_Hole_Detection_Comparison_Dataset/23997993/1?file=42085731) was used to further benchmark our coronal hole models. We used these 29 images along with masks from CHRONNOS algorithm by [Jarolim et al. (2021)](https://github.com/RobertJaro/MultiChannelCHDetection). This dataset is included in the appendices and can be used for testing of the model without additional downloads.

# Models and Jupyter notebooks

* Two best performing models based on SCSS-Net are included. Notebooks "U-net_AR.ipynb" and "U-net_CH.ipynb" make replication or alteration of the models possible along with their evaluation and visualization of predictions.

* Notebooks "U-net_AR_evaluation_only.ipynb" and "U-net_CH_evaluation_only.ipynb" are as their names suggest, just for evaluation and visualization of the predictions. Compared to the legacy notebooks, these ones were simplified for ease of use.

* To run the notebooks, simply install the required dependencies below and open the .ipynb files in Jupyter Notebook or JupyterLab. All paths to datasets are relative and should work if the structure is preserved. Each notebook is thoroughly commented, and explanatory Markdown cells are provided throughout to guide the user through each step of preprocessing, training, evaluation and visualization.

# System Requirements

 The following Python libraries are required to run the project and reproduce the experiments. These dependencies closely follow the ones from SCSS-Net:

- `albumentations >= 0.4.6` – advanced data augmentation
- `opencv-python >= 4.3.0.36` – image processing and transformation
- `matplotlib >= 3.2.1` – visualization of data and results
- `numpy >= 1.18.4` – numerical computations
- `pillow >= 7.2.0` – image file manipulation
- `tensorflow >= 2.2.0` – deep learning framework for model training
- `scikit-learn >= 0.21.3` – evaluation metrics and ML utilities
- `sunpy >= 1.1.3` – solar physics data analysis
- `astropy >= 4.0.1` – astronomical data handling and FITS support
- `zeep >= 3.4.0` – SOAP client for external data services
- `glymur >= 0.9.1` – support for JPEG2000 solar images
- `drms >= 0.5.7` – access to JSOC data services via DRMS API
- `keras-preprocessing` – preprocessing utilities for training
