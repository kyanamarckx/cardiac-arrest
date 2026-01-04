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
[mg/dl] *(note: on Kaggle it says mm/dl, but I assume this is wrong because normally cholesterol is measured in mg/dl)*

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


### Clinical feature descriptions (except ``Age``, ``Sex`` and ``HeartDisease``)
#### Chest pain type (ChestPainType)
``ChestPainType`` describes the type of chest pain experienced by the patient during physical activity or at rest. Chest pain is a key symptom used in the diagnosis of heart disease.

##### Possible values
- **TA (Typical Angina):**
  - Classic chest pain related to myocardial ischemia, usually triggered by extertion and relieved by rest
- **ATA (Atypical Angina):**
  - Chest pain that does not meet all criteria of typical angina but may still be cardiac-related
- **NAP (Non-Anginal Pain):**
  - Chest pain that is unlikely to be caused by heart disease
- **ASY (Asymptomatic):**
  - No chest pain symptoms, despite possible underlying heart disease

##### Clinical relevance
Typical and asymptomatic chest pain types are strongly associated with heart disease risk.

#### Resting blood pressure (RestingBP)
``RestingBP`` represents the patient's resting systolic blood pressure measured in millimeters of mercury (mm Hg).

##### Clinical relevance
- Normal systolic blood pressure is typically below 120 mm Hg
- Elevated blood pressure increases the workload of the heart and is a major risk factor for cardiovascular disease

##### Data considerations
Extremely low or zero values are physiologically implausible and may indicate measurement or data-entry errors.

#### Cholesterol
``Cholesterol`` refers to the serum cholesterol level measured in milligrams per deciliter (mg/dl).

##### Clinical relevance
- High cholesterol contributes to plaque formation in arteries (atherosclerosis)
- This increases the risk of coronary artery disease and heart attacks

##### Data considerations
- Zero or extremely low cholesterol values are medically unrealistic and should be carefully examined during preprocessing
- The feature often shows a skewed distribution with possible outliers

#### Fasting blood sugar (FastingBP)
``FastingBS`` indicates whether the patient's fast blood sugar level exceeds 120 mg/dl.

##### Values
- **0:**
  - Fasting blood sugar &le; 120 mg/dl
- **1:**
  - Fasting blood sugar &gt; 120 mg/dl

##### Clinical relevance
- Elevated fasting blood sugar is associated with diabetes
- Diabetes is a well-knows risk factor for cardiavascular disease

#### Resting electrocardiagram (RestingECG)
``RestingECG`` describes the results of an electrocadriagram (ECG) perfromed while the patient is at rest.

##### Possible values
- **Normal:**
  - No significant ECG abnormalities
- **ST:**
  - ST-T wave abnormalities, which may indicate ischemia
- **LVH:**
  - Left ventricular hypertrpohy, often caused by chronic high blood pressure

##### Clinical relevance
- Abnormal resting ECG findings can indicate structural or electrical heart problems.

#### Exercise angina (ExerciseAngina)
``ExerciseAngina`` indicates whether the patient experiences angina (chest pain) during physical exercise.

##### Values
- **Y:**
  - The patient experiences angina
- **N:**
  - The patient doesn't experience angina

##### Clinical relevance
- Exercise-induced angina is a strond indicator of reduced blood flow to the heart
- It is commonly associated with coronary artery disease

#### Oldpeak
``Oldpeak`` measures the amount of ST-segment depression induced by exercise relative to rest, expressed in millimeters (mm)

##### Clinical relevance
- ST-segment depression during exercise indicates myocardial ischemia
- Higher Oldpeak values are associated with more severe heart disease

##### Data considerations
- Oldpeak often has a right-skewed distribution
- High values may represent clinically severe cases rather than noise

#### ST slope (ST_Slope)
``ST_Slope`` describes the slope of the ST segment during peak exercise.

##### Possible values
- **Up:**
  - Upsloping ST segment (generally normal)
- **Flat:**
  - Flat ST segment (suspicious)
- **Down:**
  - Downsloping ST segment (highly indicative of ischemia)

##### Clinical relevance
- Flat and downsloping ST segments are strongly associated with heart disease
- ST_Slope complements Oldpeak in assessing exercise-induced ECG changes

#### Extra: relationship between Oldpeak and ST_Slope
``Oldpeak`` and ``ST_Slope`` are closely related indicators of exercise-induced myocardial ischemia:
- Low Oldpeak with an upsloping ST segment is typically observed in healthy individuals
- High Oldpeak combined with a flat or downsloping ST segment indicates increased cardiovascular risk

This relationship makes these features particularly informative for machine learning models.

### Plot explanations and conclusions
#### Kernel density plot
Shows the counts of the numerical features. The title per plot contains the skewness of the values.<br>

- **Age:** 
  - Skewness = -0,2
  - Almost symmetrical distribution, note that the range of the ages goes from 28 years to 77 years
- **RestingBP:**
  - Skewness = 0,18
  - Symmetrical distribution BUT we can see values that are probably not correct (left side of the curve)
- **Cholesterol:**
  - Skewness = -0,61
  - In general it looks relatively normal distributed, with an exception of a bunch of zero-values which are also not correct, so we definitely have a left-skewed distribution
- **FastingBS:**
  - Skewness = 1,26
  - Left-skewed distribution because there are more patients that have a fasting blood sugar lower than 120 mg/dl - this can be skipped because it is a binary feature
- **MaxHR:**
  - Skewness = 0,14
  - Symmetrical distribution
- **Oldpeak:**
  - Skewness = 1,02
  - Definitely a right-skewed distribution
- **HeartDisease:**
  - Skewness = 0,22
  - Almost symmetrical distribution, a little more patients have a heart disease than those who don't have one - this can be skipped because it is a binary feature

#### Pairplot


## 02-preprocessing.ipynb


## 03-modeling.ipynb


## 04-evaluation.ipynb

