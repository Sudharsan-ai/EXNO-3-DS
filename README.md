## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
   ```python
import pandas as pd
df = pd.read_csv("Encoding Data.csv")
df
```





<div id="df-256f8e5a-4f90-467e-b42a-736c5bf558eb" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>nom_0</th>
<th>ord_2</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Hot</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Blue</td>
<td>Warm</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Cold</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>F</td>
<td>N</td>
<td>Green</td>
<td>Warm</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>T</td>
<td>N</td>
<td>Green</td>
<td>Hot</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Warm</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Red</td>
<td>Hot</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_7b0ed9f1-bf99-40de-afe4-5315b3d1c6bd">
</div>

</div>
</div>





```python
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=["Hot","Warm","Cold"]
e1 = OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```




array([[0.],
[1.],
[2.],
[1.],
[2.],
[0.],
[2.],
[2.],
[1.],
[0.]])




```python
df["bo_1"]=e1.fit_transform(df[["ord_2"]])
df
```





<div id="df-1f66e9cb-ae4f-48fb-ae10-3c7628901d06" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>nom_0</th>
<th>ord_2</th>
<th>bo_1</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Hot</td>
<td>0.0</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Blue</td>
<td>Warm</td>
<td>1.0</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Cold</td>
<td>2.0</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>F</td>
<td>N</td>
<td>Green</td>
<td>Warm</td>
<td>1.0</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>T</td>
<td>N</td>
<td>Green</td>
<td>Hot</td>
<td>0.0</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Warm</td>
<td>1.0</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Red</td>
<td>Hot</td>
<td>0.0</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_5a4f27cc-9c1d-4c30-9fa9-6dc305acd8be">
</div>

</div>
</div>





```python
dfc=df.copy()
le = LabelEncoder()
le.fit_transform(dfc[["ord_2"]])
```

/usr/local/lib/python3.12/dist-packages/sklearn/preprocessing/_label.py:110: DataConversionWarning: A column-vector y was passed when a 1d array was expected. Please change the shape of y to (n_samples, ), for example using ravel().
y = column_or_1d(y, warn=True)





array([1, 2, 0, 2, 0, 1, 0, 0, 2, 1])




```python
dfc["bo_1"]=le.fit_transform(df[["ord_2"]])
dfc
```

/usr/local/lib/python3.12/dist-packages/sklearn/preprocessing/_label.py:110: DataConversionWarning: A column-vector y was passed when a 1d array was expected. Please change the shape of y to (n_samples, ), for example using ravel().
y = column_or_1d(y, warn=True)






<div id="df-93fd685e-2a3a-4076-9d07-58af71a83695" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>nom_0</th>
<th>ord_2</th>
<th>bo_1</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Hot</td>
<td>1</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Blue</td>
<td>Warm</td>
<td>2</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Cold</td>
<td>0</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>F</td>
<td>N</td>
<td>Green</td>
<td>Warm</td>
<td>2</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>0</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>T</td>
<td>N</td>
<td>Green</td>
<td>Hot</td>
<td>1</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>0</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>0</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Warm</td>
<td>2</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Red</td>
<td>Hot</td>
<td>1</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_8653d30d-a6f1-4c63-bdde-547ae6187d77">
</div>

</div>
</div>





```python
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder(sparse_output=False)
df1 = df.copy()
enc = pd.DataFrame(ohe.fit_transform(df1[["nom_0"]]))
enc

```





<div id="df-d35a9629-44f9-4a6c-a3e2-e7c9c30ebb32" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>0</th>
<th>1</th>
<th>2</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>1</th>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>2</th>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>3</th>
<td>0.0</td>
<td>1.0</td>
<td>0.0</td>
</tr>
<tr>
<th>4</th>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>5</th>
<td>0.0</td>
<td>1.0</td>
<td>0.0</td>
</tr>
<tr>
<th>6</th>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>7</th>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>8</th>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>9</th>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_ed8392b5-e2ab-49b9-aa2c-3fe16171ad7f">
</div>

</div>
</div>





```python
df1=pd.concat((df1,enc),axis=1)
df1
```





<div id="df-50827c45-3c10-4f0d-9320-9853ddaaaa3d" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>nom_0</th>
<th>ord_2</th>
<th>bo_1</th>
<th>0</th>
<th>1</th>
<th>2</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Hot</td>
<td>0.0</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Blue</td>
<td>Warm</td>
<td>1.0</td>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Cold</td>
<td>2.0</td>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>F</td>
<td>N</td>
<td>Green</td>
<td>Warm</td>
<td>1.0</td>
<td>0.0</td>
<td>1.0</td>
<td>0.0</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>T</td>
<td>N</td>
<td>Green</td>
<td>Hot</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
<td>0.0</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>F</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>T</td>
<td>N</td>
<td>Red</td>
<td>Cold</td>
<td>2.0</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>F</td>
<td>N</td>
<td>Blue</td>
<td>Warm</td>
<td>1.0</td>
<td>1.0</td>
<td>0.0</td>
<td>0.0</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Red</td>
<td>Hot</td>
<td>0.0</td>
<td>0.0</td>
<td>0.0</td>
<td>1.0</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_7d9f3bc0-5e37-44d9-b1e4-473a8c9c6c24">
</div>

</div>
</div>





```python
pip install --upgrade category_encoders

```

Collecting category_encoders
Downloading category_encoders-2.9.0-py3-none-any.whl.metadata (7.9 kB)
Requirement already satisfied: numpy>=1.14.0 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (2.0.2)
Requirement already satisfied: pandas>=1.0.5 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (2.2.2)
Requirement already satisfied: patsy>=0.5.1 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (1.0.2)
Requirement already satisfied: scikit-learn>=1.6.0 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (1.6.1)
Requirement already satisfied: scipy>=1.0.0 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (1.16.3)
Requirement already satisfied: statsmodels>=0.9.0 in /usr/local/lib/python3.12/dist-packages (from category_encoders) (0.14.6)
Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.12/dist-packages (from pandas>=1.0.5->category_encoders) (2.9.0.post0)
Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.12/dist-packages (from pandas>=1.0.5->category_encoders) (2025.2)
Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.12/dist-packages (from pandas>=1.0.5->category_encoders) (2025.3)
Requirement already satisfied: joblib>=1.2.0 in /usr/local/lib/python3.12/dist-packages (from scikit-learn>=1.6.0->category_encoders) (1.5.3)
Requirement already satisfied: threadpoolctl>=3.1.0 in /usr/local/lib/python3.12/dist-packages (from scikit-learn>=1.6.0->category_encoders) (3.6.0)
Requirement already satisfied: packaging>=21.3 in /usr/local/lib/python3.12/dist-packages (from statsmodels>=0.9.0->category_encoders) (26.0)
Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.12/dist-packages (from python-dateutil>=2.8.2->pandas>=1.0.5->category_encoders) (1.17.0)
Downloading category_encoders-2.9.0-py3-none-any.whl (85 kB)
[2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m85.9/85.9 kB[0m [31m2.8 MB/s[0m eta [36m0:00:00[0m
[?25hInstalling collected packages: category_encoders
Successfully installed category_encoders-2.9.0



```python
pd.get_dummies(df,columns=["nom_0"])
```





<div id="df-88b3ee4a-1950-42d9-b773-e1d7e68de75e" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>ord_2</th>
<th>bo_1</th>
<th>nom_0_Blue</th>
<th>nom_0_Green</th>
<th>nom_0_Red</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Hot</td>
<td>0.0</td>
<td>False</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Warm</td>
<td>1.0</td>
<td>True</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>F</td>
<td>N</td>
<td>Cold</td>
<td>2.0</td>
<td>True</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>F</td>
<td>N</td>
<td>Warm</td>
<td>1.0</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>T</td>
<td>N</td>
<td>Cold</td>
<td>2.0</td>
<td>False</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>T</td>
<td>N</td>
<td>Hot</td>
<td>0.0</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>F</td>
<td>N</td>
<td>Cold</td>
<td>2.0</td>
<td>False</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>T</td>
<td>N</td>
<td>Cold</td>
<td>2.0</td>
<td>False</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>F</td>
<td>N</td>
<td>Warm</td>
<td>1.0</td>
<td>True</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Hot</td>
<td>0.0</td>
<td>False</td>
<td>False</td>
<td>True</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


</div>
</div>





```python
from category_encoders import BinaryEncoder
da = pd.read_csv("data.csv")
da
```





<div id="df-bf0f89bb-ab24-476c-8bc1-22eca82ef204" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>City</th>
<th>Ord_1</th>
<th>Ord_2</th>
<th>Target</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Hot</td>
<td>High School</td>
<td>0</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Bangalore</td>
<td>Warm</td>
<td>Masters</td>
<td>1</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>M</td>
<td>N</td>
<td>Mumbai</td>
<td>Very Hot</td>
<td>Diploma</td>
<td>1</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>M</td>
<td>Y</td>
<td>Chennai</td>
<td>Cold</td>
<td>Bachelors</td>
<td>0</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>M</td>
<td>Y</td>
<td>Delhi</td>
<td>Cold</td>
<td>Bachelors</td>
<td>1</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>Masters</td>
<td>0</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>M</td>
<td>N</td>
<td>Chennai</td>
<td>Warm</td>
<td>PhD</td>
<td>1</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>F</td>
<td>N</td>
<td>Chennai</td>
<td>Hot</td>
<td>High School</td>
<td>1</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>M</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>High School</td>
<td>0</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Delhi</td>
<td>Warm</td>
<td>PhD</td>
<td>0</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_4b75d9e5-924f-4df1-8772-e2e2bb0dd055">
</div>

</div>
</div>





```python
be = BinaryEncoder()
dac=da.copy()
benc=be.fit_transform(dac["City"])
benc
```





<div id="df-7b7f2799-1e68-45cc-b4f8-6302930f90ba" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>City_0</th>
<th>City_1</th>
<th>City_2</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>1</th>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr>
<th>2</th>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<th>3</th>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>4</th>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>5</th>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>6</th>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>7</th>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>8</th>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>9</th>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_c83628ea-5d5e-4996-a40e-f36c9aa8cb29">
</div>

</div>
</div>





```python
dac=pd.concat((dac,benc),axis=1)
dac
```





<div id="df-ab30122e-e63a-4000-baad-09a159e8cae2" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>City</th>
<th>Ord_1</th>
<th>Ord_2</th>
<th>Target</th>
<th>City_0</th>
<th>City_1</th>
<th>City_2</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Hot</td>
<td>High School</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Bangalore</td>
<td>Warm</td>
<td>Masters</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>M</td>
<td>N</td>
<td>Mumbai</td>
<td>Very Hot</td>
<td>Diploma</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>M</td>
<td>Y</td>
<td>Chennai</td>
<td>Cold</td>
<td>Bachelors</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>M</td>
<td>Y</td>
<td>Delhi</td>
<td>Cold</td>
<td>Bachelors</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>Masters</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>M</td>
<td>N</td>
<td>Chennai</td>
<td>Warm</td>
<td>PhD</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>F</td>
<td>N</td>
<td>Chennai</td>
<td>Hot</td>
<td>High School</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>M</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>High School</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Delhi</td>
<td>Warm</td>
<td>PhD</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_30085b29-ef01-4b13-bd0f-477be95054a3">
</div>

</div>
</div>





```python
from category_encoders import TargetEncoder
te = TargetEncoder()
da1 = da.copy()
tenc=te.fit_transform(da1["City"],da1["Target"])
tenc
```





<div id="df-0b5ebca2-acf8-48b9-ac34-77c3287e9c7b" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>City</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0.445272</td>
</tr>
<tr>
<th>1</th>
<td>0.565054</td>
</tr>
<tr>
<th>2</th>
<td>0.565054</td>
</tr>
<tr>
<th>3</th>
<td>0.525744</td>
</tr>
<tr>
<th>4</th>
<td>0.445272</td>
</tr>
<tr>
<th>5</th>
<td>0.445272</td>
</tr>
<tr>
<th>6</th>
<td>0.525744</td>
</tr>
<tr>
<th>7</th>
<td>0.525744</td>
</tr>
<tr>
<th>8</th>
<td>0.445272</td>
</tr>
<tr>
<th>9</th>
<td>0.445272</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_1260ddce-5e3d-4a39-a853-45c1c418ae3a">
</div>

</div>
</div>





```python
da1=pd.concat((da1,tenc),axis=1)
da1
```





<div id="df-5c41cc7d-1466-4eda-9fd2-6f87dc50f6d1" class="colab-df-container">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>id</th>
<th>bin_1</th>
<th>bin_2</th>
<th>City</th>
<th>Ord_1</th>
<th>Ord_2</th>
<th>Target</th>
<th>City</th>
<th>City</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>0</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Hot</td>
<td>High School</td>
<td>0</td>
<td>0.445272</td>
<td>0.445272</td>
</tr>
<tr>
<th>1</th>
<td>1</td>
<td>F</td>
<td>Y</td>
<td>Bangalore</td>
<td>Warm</td>
<td>Masters</td>
<td>1</td>
<td>0.565054</td>
<td>0.565054</td>
</tr>
<tr>
<th>2</th>
<td>2</td>
<td>M</td>
<td>N</td>
<td>Mumbai</td>
<td>Very Hot</td>
<td>Diploma</td>
<td>1</td>
<td>0.565054</td>
<td>0.565054</td>
</tr>
<tr>
<th>3</th>
<td>3</td>
<td>M</td>
<td>Y</td>
<td>Chennai</td>
<td>Cold</td>
<td>Bachelors</td>
<td>0</td>
<td>0.525744</td>
<td>0.525744</td>
</tr>
<tr>
<th>4</th>
<td>4</td>
<td>M</td>
<td>Y</td>
<td>Delhi</td>
<td>Cold</td>
<td>Bachelors</td>
<td>1</td>
<td>0.445272</td>
<td>0.445272</td>
</tr>
<tr>
<th>5</th>
<td>5</td>
<td>F</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>Masters</td>
<td>0</td>
<td>0.445272</td>
<td>0.445272</td>
</tr>
<tr>
<th>6</th>
<td>6</td>
<td>M</td>
<td>N</td>
<td>Chennai</td>
<td>Warm</td>
<td>PhD</td>
<td>1</td>
<td>0.525744</td>
<td>0.525744</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>F</td>
<td>N</td>
<td>Chennai</td>
<td>Hot</td>
<td>High School</td>
<td>1</td>
<td>0.525744</td>
<td>0.525744</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>M</td>
<td>N</td>
<td>Delhi</td>
<td>Very Hot</td>
<td>High School</td>
<td>0</td>
<td>0.445272</td>
<td>0.445272</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>F</td>
<td>Y</td>
<td>Delhi</td>
<td>Warm</td>
<td>PhD</td>
<td>0</td>
<td>0.445272</td>
<td>0.445272</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">


</div>


<div id="id_f6520ec5-ce2a-4e0a-8183-7382c9c04c90">
</div>

</div>
</div>





```python

```

# RESULT:
       # INCLUDE YOUR RESULT HERE

       
