# Exno:1 Data Cleaning Process using python

# Name:Piritharaman R
# Reg no: 212223230148

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

# Coding and Output:

import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
![WhatsApp Image 2024-08-21 at 8 50 02 PM](https://github.com/user-attachments/assets/5cbc5b85-b378-4fac-9a0d-9801f575a546)

df.isnull().sum()
![WhatsApp Image 2024-08-21 at 8 51 19 PM](https://github.com/user-attachments/assets/64fa6f07-b56c-47af-9a68-bc230e4a0230)

df.isnull().any()
![WhatsApp Image 2024-08-21 at 8 52 33 PM](https://github.com/user-attachments/assets/c315f1da-b37d-4ce2-bc05-352d93e25289)

df.dropna()
![WhatsApp Image 2024-08-21 at 8 53 42 PM](https://github.com/user-attachments/assets/d2b92284-5ccb-4c85-9375-e9e8ec92e9e7)

df.fillna(0)
![WhatsApp Image 2024-08-21 at 8 54 45 PM](https://github.com/user-attachments/assets/b6ed2f12-be86-479b-b443-818f9eacad82)
![WhatsApp Image 2024-08-21 at 8 55 24 PM](https://github.com/user-attachments/assets/b6f5982d-a7e7-4267-bb38-0910e69b42e9)

df.fillna(method = 'ffill')
![WhatsApp Image 2024-08-21 at 8 59 29 PM](https://github.com/user-attachments/assets/4c8f96d0-cb3a-4a2e-baa6-4cd385b915ca)
![WhatsApp Image 2024-08-21 at 8 59 30 PM](https://github.com/user-attachments/assets/d8008db1-e310-41c8-a659-195efa4ded1e)

df.fillna(method = 'bfill'
![WhatsApp Image 2024-08-21 at 9 01 41 PM](https://github.com/user-attachments/assets/0d964e56-9137-42a0-a371-18a89c5c5c58)
![WhatsApp Image 2024-08-21 at 9 02 10 PM](https://github.com/user-attachments/assets/155b7027-1187-4101-90da-26c522916978)

df_dropped = df.dropna()
df_dropped
![WhatsApp Image 2024-08-21 at 9 03 10 PM](https://github.com/user-attachments/assets/e958e35b-6892-41d7-b41f-b2aa96b08b0f)

df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':92,'TOTAL':305,'AVG':89.999999})
![WhatsApp Image 2024-08-21 at 9 04 19 PM](https://github.com/user-attachments/assets/08da8c43-8e60-4cbf-9021-72a1f08c8bd8)
![WhatsApp Image 2024-08-21 at 9 05 02 PM](https://github.com/user-attachments/assets/f5bf4187-c516-48ed-b46e-4fa405b00e46)

import pandas as pd
ir=pd.read_csv('/content/iris (1).csv')
ir
![WhatsApp Image 2024-08-21 at 9 05 52 PM](https://github.com/user-attachments/assets/3cf8f3a9-14b3-450b-ba85-ad00dc6fbd50)

ir.describe()
![WhatsApp Image 2024-08-21 at 9 08 19 PM](https://github.com/user-attachments/assets/0560dbaf-6e03-4ff1-9a18-5af1ba3e6bd6)

import pandas as pd
import seaborn as sns
import numpy as np
sns.boxplot(x='sepal_width',data=ir)
![WhatsApp Image 2024-08-21 at 9 09 22 PM](https://github.com/user-attachments/assets/7908205a-570d-4b11-9f41-54ee79cd2ba2)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
![WhatsApp Image 2024-08-21 at 9 10 34 PM](https://github.com/user-attachments/assets/05a67cb3-7c1c-450f-ab44-6b65db050687)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
![WhatsApp Image 2024-08-21 at 9 11 38 PM](https://github.com/user-attachments/assets/5ab0bb16-81e5-4310-b901-29cabe658880)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
![WhatsApp Image 2024-08-21 at 9 12 39 PM](https://github.com/user-attachments/assets/a48344dc-bafc-4221-bb41-427fc9061ade)

sns.boxplot(x='sepal_width',data=delid)
![WhatsApp Image 2024-08-21 at 9 13 54 PM](https://github.com/user-attachments/assets/02d961d2-732a-4613-a5b6-b0a3847ad721)

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
![WhatsApp Image 2024-08-21 at 9 15 06 PM](https://github.com/user-attachments/assets/2a3942aa-99f2-4787-a21f-af5888778b9e)

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
![WhatsApp Image 2024-08-21 at 9 15 55 PM](https://github.com/user-attachments/assets/2bdb81cb-fa62-45fa-bde8-5a8bfb6d6628)

low = q1 - 1.5*iqr
low
![WhatsApp Image 2024-08-21 at 9 17 02 PM](https://github.com/user-attachments/assets/27c461d3-8812-4d74-9e8e-60d4867eca7a)

high = q3 + 1.5*iqr
high
![WhatsApp Image 2024-08-21 at 9 18 08 PM](https://github.com/user-attachments/assets/67c7f429-8732-4e7c-addc-99ac02f28e94)

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
![WhatsApp Image 2024-08-21 at 9 19 02 PM](https://github.com/user-attachments/assets/b2407eb2-b27c-4964-9562-0bfd827e9a7f)

z = np.abs(stats.zscore(df['height']))
z
![WhatsApp Image 2024-08-21 at 9 20 02 PM](https://github.com/user-attachments/assets/e77e18e4-e140-4a90-a374-33f7f613924f)

df1 = df[z<3]
df1
![image](https://github.com/user-attachments/assets/7746f5c4-cfda-41bf-bdab-3781dc72b4c5)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
