# :love_letter: Notes and conclusions of the notebooks

## 01-exploration.ipynb
### General
- 918 entries & 12 columns
- 7 numerical (6 int64 + 1 float64) and 5 categorical
- No null-values available
- More data availble of men than women (725 vs 193)
- 508 entries have a heart disease (1), 410 don't have one (0)

### Column explanations (information retrieved from Kaggle)
#### Age
Age of the patient<br>
[years]

#### Sex
Sex of the patient<br>
[M: Male, F: Female]

#### ChestPainType
Chest pain type<br>
[TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic]

#### RestingBP
Resting blood pressure<br>
[mm Hg]

#### Cholesterol
Serum cholesterol<br>
[mm/dl]

#### FastingBS
Fasting blood sugar<br>
[1: if FastingBS > 120 mg/dl, 0: otherwise]

#### RestingECG
Resting electrocardiagram results<br>
[Normal: Normal, ST: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV), LVH: showing probable or definite left ventricular hypertrophy by Estes' criteria]

#### MaxHR
Maximum heart rate achieved<br>
[Numeric value between 60 and 202]

#### ExerciseAngina
Exercise-induced angina<br>
[Y: Yes, N: No]

#### Oldpeak
Oldpeak = ST<br>
[Numeric value measured in depression]

#### ST_Slope
The slope of the peak exercise ST segment<br>
[Up: upsloping, Flat: flat, Down: downsloping]

#### HeartDisease
Output class (target)<br>
[1: heart disease, 0: normal]


### Extra information about the columns



### Plot explanations and conclusions
#### Kernel density plot
Shows the counts of the numerical features. The title per plot contains the skewness of the values.<br>

- **Age:** skewness = -0,2 ; almost symmetrical distribution, note that the range of the ages goes from 28 years to 77 years<br>
- **RestingBP:** skewness = 0,18 ; symmetrical distribution BUT we can see values that are probably not correct (left side of the curve)<br>
- **Cholesterol:** skewness = -0,61 ; in general it looks relatively normal distributed, with an exception of a bunch of zero-values which are also not correct, so we definitely have a left skewed distribution<br>
- **FastingBS:** skewness = 1,26 ; left skewed distribution because there are more patients that have a fasting blood sugar lower than 120 mg/dl - this can be skipped because it is a binary feature<br>
- **MaxHR:** skewness = 0,14 ; symmetrical distribution<br>
- **Oldpeak:** skewness = 1,02 ; definitely a right skewed distribution
- **HeartDisease:** skewness = 0,22 ; almost symmetrical distribution, a little more patients have a heart disease than those who don't have one

#### Pairplot


## 02-preprocessing.ipynb


## 03-modeling.ipynb


## 04-evaluation.ipynb

