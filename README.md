# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/5f71fb9b-4c91-4016-a46f-da7bc2afd12f)

```
df.isnull().sum()
```

![image](https://github.com/user-attachments/assets/8f76292c-6f0c-43e6-8357-52b518afd56f)

```
df.isnull().any()
```

![image](https://github.com/user-attachments/assets/b8cb672e-b1c1-4f90-9d31-8da672cbbcfc)

```
df.dropna()
```

![image](https://github.com/user-attachments/assets/6011f4f6-5125-4736-a685-69a5578986ed)

```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/4f8c8c24-2f5d-48ca-875f-83ae3c85b8fb)

```
df.fillna(method = "ffill")
```

![image](https://github.com/user-attachments/assets/36a231c7-0453-4d72-9e8e-b84f7230ec66)

```
df.fillna(method = "bfill")
```

![image](https://github.com/user-attachments/assets/6a9a986c-8d8c-4442-8952-8a93cfc1181f)

```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/e38b407c-1d3b-485e-b083-6f89d5fd70df)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

![image](https://github.com/user-attachments/assets/0bb19a32-5f87-4788-b039-1f43c65245f0)

IQR(Inter Quartile Range)

```
ir = pd.read_csv("/content/iris (1).csv")
ir
```

![image](https://github.com/user-attachments/assets/9b492901-1fc5-4bbf-aa0c-44b793c95cc9)

```
ir.describe()
```

![image](https://github.com/user-attachments/assets/7ba73def-381e-4e2c-9971-4030e69ea5f9)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/2d4688db-5512-4f96-be68-4e0daa62ae3f)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```

![image](https://github.com/user-attachments/assets/8c733cd9-3ea6-4123-90f7-c11274e3ad6e)

```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/d98011b5-f4bc-45f3-a5cb-17b29a0b489c)

```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/d077bce2-8c0a-4079-bb0c-c48989cd1046)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/36ca38ae-e1b3-43f6-bbfe-782b85e2fbcf)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```

```
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/08185fcd-afd5-4bee-b6dc-48b2fd03dda3)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/80c5783e-2c09-4dea-9b8b-bef10296ad36)

```
low = q1- 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/e8f20d69-a9a2-4f6b-b6a0-b0805ce448f1)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/91c10463-9a5b-4cbf-95f1-44d00561c061)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/18e8a851-8596-4c27-91f0-7c83beb50f6e)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/54ba5ace-d11f-49bc-b0de-2495cd2def47)

```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/f939862d-814d-4942-aa9e-97d60ffe4517)


# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
