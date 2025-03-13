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
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
```
![image](https://github.com/user-attachments/assets/fb40c9e1-91ca-41a8-a73f-11a8c6901a24)
```
         df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/448b4773-bb27-42e1-b8bd-bb59948d6823)
```
         df.isnull().any()
```
![image](https://github.com/user-attachments/assets/0387ae9d-9e4b-405b-adbb-79b212f13439)
```
         df.dropna()
```
![image](https://github.com/user-attachments/assets/918ac1d7-18d2-4ebd-8a82-3ab2a7d7ff07)
```
         df.fillna(0)
```
![image](https://github.com/user-attachments/assets/d7860d8e-28f3-4776-8bd2-bc55fb3b9f0a)
```
         df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/77708935-1910-4d3a-94ba-02fadf5766ba)
```
         df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/3cc33a87-b6cc-4b9a-a590-dcf4c31a99af)
```
         df_dropped = df.dropna()
           df_dropped
```
![image](https://github.com/user-attachments/assets/87cca6f6-713d-44af-91db-bbd88a5a7abb)
```
         df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/a527569f-b8ca-42b8-8d46-00443f376a75)
```
         import pandas as pd
         
         ir=pd.read_csv('iris.csv')
         ir
```
![image](https://github.com/user-attachments/assets/24a5f2e3-1de1-48d2-a6f3-d1443fed5817)
```
         ir.describe()
```
![image](https://github.com/user-attachments/assets/636168ab-1f13-4cf8-9f82-ad3f4af92596)
```         import seaborn as sns
         
         sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/a589836b-43b2-4361-8d33-29417ffc00e8)
```
           c1=ir.sepal_width.quantile(0.25)
           c3=ir.sepal_width.quantile(0.75)
           iq=c3-c1
           print(c3)
```
```
            rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/bceb96f4-fc58-49d8-a648-fe05f688cf8e)
```
            delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            delid
```
![image](https://github.com/user-attachments/assets/f9b991b0-b896-47a9-a1e1-4b091d727d6b)
```
           sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/eaf1ca13-2023-429a-92e1-50320226151d)

```
            import matplotlib.pyplot as plt
            import pandas as pd
            import numpy as np
            import scipy.stats as stats

            dataset=pd.read_csv("heights.csv")
            dataset
```
![image](https://github.com/user-attachments/assets/8a67ad73-93d4-46a4-b449-df5803bc4b52)
```
            df = pd.read_csv("heights.csv")
            q1 = df['height'].quantile(0.25)
            q2 = df['height'].quantile(0.5)
            q3 = df['height'].quantile(0.75)
            
            iqr = q3-q1
            iqr
```
![image](https://github.com/user-attachments/assets/f6ff638f-d523-4a4f-93ca-5ee98f2ee8c8)
```
        low = q1 - 1.5*iqr
        low
```
![image](https://github.com/user-attachments/assets/fc764ba2-2a21-4896-a625-0b2a5df21f53)
```
        high = q3 + 1.5*iqr
        high
```
![image](https://github.com/user-attachments/assets/c66570bd-4ed8-45c9-b213-bba4edd76b50)
```
        df1 = df[((df['height'] >=low)& (df['height'] <=high))]
        df1
```
![image](https://github.com/user-attachments/assets/3258b404-9cf0-4954-aee7-12c26f170dc5)
```
        z = np.abs(stats.zscore(df['height']))
        z
```
![image](https://github.com/user-attachments/assets/d4300244-7eec-41cb-8043-8672d8e9cd2f)

```
        df1 = df[z<3]
        df1
```
![image](https://github.com/user-attachments/assets/8b319dcc-a714-4b7b-974b-11cf96134829)

# Result
      Hence the data was cleaned , outliers were detected and removed.
