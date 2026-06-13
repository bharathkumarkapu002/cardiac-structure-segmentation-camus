# Project Title

Generalisable Deep Learning for Cardiac Structure Segmentation Using Echocardiography



## Overview

This dissertation project develops and evaluates deep learning models for automatic cardiac structure segmentation using echocardiographic images. The work focuses on segmenting clinically important cardiac regions, including:



\- Left ventricle (LV)

\- Myocardium (MYO)

\- Left atrium (LA)



The project compares several segmentation architectures, loss functions, and sampling strategies. 
The final recorded best-performing configuration in the dissertation was: Attention U-Net + weighted sampling + focal Dice loss
with a final recorded foreground mean Dice score of: 0.899058

## Important Note About Running the Project

The final notebook was developed and tested in \*\*Google Colab\*\*. It is recommended to run the final project notebook in Google Colab because the code is written for the Colab environment and uses Colab-based commands for uploading the Kaggle API file, downloading the dataset, extracting files, and running experiments.

The Week 1 to Week 6 notebooks are included as supporting source files. They are useful for reviewing the project development process, but the final dissertation results should be reproduced from the final Week 20-epoch notebook.

The user only needs to:

1\. Open the notebook in Google Colab.

2\. Run the cells from top to bottom.

3\. When prompted, upload the provided 'kaggle.json' file.

4\. The dataset will be downloaded automatically using the Kaggle API.


## Files Provided

The project submission includes the final notebook and the earlier weekly development notebooks.

Week 1 notebook

Week 2 notebook

Week 3 notebook

Week 4 notebook

Week 5 notebook

Week 6 notebook

07\_Final\_20Epochs\_Experiment\_Week10\_Apr04\_UPDATED.ipynb

README.txt

kaggle.json


The Week 1 to Week 6 notebooks are included as development/source files to show the progression of the project. These files document the earlier stages of experimentation, including baseline model development, preprocessing, model improvements, sampling and loss-function experiments, and intermediate testing.


The main final notebook to run for the dissertation results is: 07\_Final\_20Epochs\_Experiment\_Week10\_Apr04\_UPDATED.ipynb



The kaggle.json file is required for dataset downloading through the Kaggle API.

## Dataset Download Method

The dataset is downloaded automatically inside the notebook using the Kaggle API.

### The notebook includes code similar to:

from google.colab import files

uploaded = files.upload()

!pip install -q kaggle

!mkdir -p \~/.kaggle

!cp kaggle.json \~/.kaggle/

!chmod 600 \~/.kaggle/kaggle.json

!kaggle datasets download -d shoybhasan/camus-human-heart-data -p /content --force

After downloading, the dataset is extracted and organised automatically by the notebook.

The dataset root used in the notebook is: root\_dir = "/content/camus\_full/database\_nifti"

## How to Run the Notebook in Google Colab

Step 1: Open Google Colab

Open Google Colab in a browser.

Step 2: Upload the Final Notebook

Upload and open the final notebook: 07\_Final\_20Epochs\_Experiment\_Week10\_Apr04\_UPDATED.ipynb

The Week 1 to Week 6 notebooks are provided for reference and project traceability. They do not need to be run to reproduce the final dissertation results.

Step 3: Run the First Dataset Setup Cell

Run the first setup cell. It will ask you to upload a file.

Step 4: Upload Kaggle API File

When the file upload button appears, select and upload: kaggle.json

This file is required for Kaggle authentication.

Step 5: Automatic Dataset Download

After uploading 'kaggle.json', the notebook will automatically:

\- Install Kaggle if required

\- Configure the Kaggle API

\- Download the CAMUS dataset from Kaggle

\- Extract the dataset

\- Set the dataset root directory

No manual dataset download is required.

Step 6: Run All Notebook Cells in Order

After the dataset is downloaded, run the remaining notebook cells from top to bottom.

## The notebook includes:

\- Library imports

\- Dataset loading

\- Data preprocessing

\- Patient-level train/validation/test split

\- Data augmentation

\- Model definitions

\- Loss functions

\- Sampling strategies

\- Model training

\- Model evaluation

\- Result tables

\- Qualitative visualisations

## Models Implemented

The notebook evaluates several deep learning segmentation architectures:

\- U-Net

\- ResUNet

\- DeepLabV3

\- Attention U-Net

\- U-Net++

## Sampling Strategies

The notebook evaluates several sampling strategies:

\- Uniform sampling

\- Weighted sampling

\- Balanced sampling

\- Improved sampler

The improved sampler is a custom adaptive sampling strategy designed to increase exposure to clinically relevant foreground structures. It considers anatomical structure size and contextual rarity so that the model sees more informative examples during training.

## Loss Functions

The notebook evaluates different loss functions and combinations, including:

\- Cross-entropy loss

\- Dice loss

\- Cross-entropy + Dice loss

\- Focal Dice loss

## Evaluation Metrics

The project evaluates segmentation performance using:

\- Foreground mean Dice score

\- Class-wise Dice score for LV, MYO, and LA

\- 95th percentile Hausdorff Distance (HD95)

\- End-Diastolic Volume Mean Absolute Error (EDV MAE)

\- End-Systolic Volume Mean Absolute Error (ESV MAE)

\- Ejection Fraction Mean Absolute Error (EF MAE)

## Final Recorded Best Result

The final recorded best-performing model configuration used in the dissertation was: Attention U-Net + weighted sampling + focal Dice loss

Final recorded foreground mean Dice score: 0.899058


Class-wise Dice scores for the best-performing model:

LV  = 0.931915

MYO = 0.868438

LA  = 0.896820

## Important Reproducibility Note

A fixed random seed was used to improve reproducibility. However, the notebook includes stochastic components such as:

\- Data augmentation

\- Sampling strategy variation

\- GPU computation

\- Runtime behaviour in Google Colab

Because of these factors, rerunning the notebook may produce small differences in the results.

The dissertation reports the final recorded outputs from the completed run.

## CSV Output Note

During experimentation, some CSV result files were generated in Google Colab. However, because of runtime/session limitations and Colab storage behaviour, these CSV files were not retained in the final runtime environment.

The final dissertation uses the recorded notebook outputs and appendix figures rather than relying on separate saved CSV files. Therefore, if the notebook is rerun, new CSV files may be generated again, but their values may differ slightly from the final recorded dissertation results because of stochastic training behaviour.

## Expected Outputs

When the notebook is run successfully, it produces:

\- Printed experiment results

\- Leaderboard-style result tables inside the notebook

\- Model performance comparison outputs

\- Segmentation visualisations

\- Example predictions from the test set

### The visual outputs include:


\- Original echocardiography image

\- Ground truth mask

\- Predicted mask

\- Ground truth overlay

\- Prediction overlay

\- Class-wise Dice scores

## Recommended Runtime

Use the following Google Colab runtime setting:

Runtime > Change runtime type > Hardware accelerator > GPU

A GPU runtime is recommended because training multiple deep learning models on 512 × 512 medical images can take a long time on CPU.

## Running Time

The full notebook trains and evaluates multiple model configurations. The total running time depends on GPU availability and Colab runtime conditions. Running the complete experiment can take a long time, so it is recommended to keep the Colab session active until all cells finish.

## Troubleshooting
### Kaggle authentication error

Make sure the uploaded file is named exactly: kaggle.json

If the file has a different name, rename it to `kaggle.json` and rerun the setup cell.

## Dataset path error

Check that the dataset root is:root\_dir = "/content/camus\_full/database\_nifti"

If extraction fails, rerun the dataset download and extraction cell.

## Runtime disconnected

If Google Colab disconnects, variables and trained models may be lost. In that case, rerun the notebook from the beginning.

## Different results after rerunning



Small differences in results are expected because of stochastic augmentation, sampling, and GPU computation. The dissertation results are based on the final recorded run.


