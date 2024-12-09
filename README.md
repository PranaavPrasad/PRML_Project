# PRML Project

## Dataset
### [Illinois DOC labeled faces dataset](https://academictorrents.com/details/4b9b7e449aa732842aea1a7d4e6413f4507aea99)
The dataset contains details of the inmates, including sex, weight, height, front face images, and side face images. It also contains the offences committed by each inmate.

## Objective 
To train models on the given dataset to do the following tasks - 
- Predict gender from the front face image of a person

- Predict BMI from the front face image of a person

Additionally, plot the number of offences commited and their count.

## Steps to run the notebooks
1. Clone the repository.

```
git clone https://github.com/PranaavPrasad/PRML_Project.git
cd PRML_Project
```

2. Download and place the dataset inside the repository.

3. Make a folder called `test_images` and place all pictures you want to make predictions on in this folder. Make sure the folder is inside the repository.

4. To create the custom dataset (custom_dataset.pkl), run all cells in the notebook `custom_dataset.ipynb`.

5. Run all cells in  `bmi.ipynb` to predict BMI values.

6. Run all cells in `gender.ipynb` to predict gender.

7. Run all cells in `distribution.ipynb` to plot the number of offences commited.

## Data Preprocessing
#### Notebook - `custom_dataset.ipynb`
#### CSV file - `person.csv`
#### image folders - `/front` and `/side`
#### Implementation
1. Reading gender of each inmate.

2. Calculating BMI of each inmate using the formulae `BMI = weight(kg) / height(m)^2`.

3. Reading the front image and side image of the inmates only if the image exists.
 - The inmate is recorded only if the front and side image is available.

 - A limit of 4000 is kept on the number of males to match match the number of females.

 - The images are resized to (512,512).

 - The images are converted to grayscale.

4. The dataset is converted to a pickle file `custom_dataset.pkl` for further use.

## Feature Detection
#### Notebook
Its is implemented in both the notebooks, `bmi.ipynb` and `gender.ipynb`. 

#### Feature Extraction
The 68 facial landmarks were used as features. The coordinates of the landmarks (x and y values) gives a total of  68 * 2 = 136 dimensions.

`dlib` library is used to extract these features.

#### Dimensionality reduction
Principal Component Analysis (PCA) is performed on these 136 dimensions to reduce the number of dimensions to 23. This captures 99.9% of the variance.

## BMI Prediction
#### Notebook - `bmi.ipynb`
#### Implementation
Linear Regression model is used with a 80-20 train-test split. The model is evaluated on the following parameters - 
- MAE

- MSE

- R2

- Pearson Coefficient

The model achieved a MAE score of 4.32.

## Gender Classification
#### Notebook - `gender.ipynb`
#### Implementation
Support vector machine (SVM) model is used with a 80-20 train-test split. The model is evaluated on the following parameters - 
- MAE

- MSE

- R2

- Pearson Coefficient

The model achieved an accuracy of 87.43%.

## Distribution of Offences
#### Notebook - `distribution.ipynb`
#### CSV file - `sentencing.csv`
#### Implementation
A count of number of times an offence is committed is displayed. As there are a lot of offences, we have plotted the offences which make up 75% of the data for easier visualisation. Additionally, the count of all offences have also been plotted.

## Authors