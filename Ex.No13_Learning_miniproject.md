# Ex.No: 13 Machine Learning 
### DATE: 25-10-2025                                                                        
### REGISTER NUMBER : 212223060312
# Water Quality Prediction Using Machine Learning

## Aim
To develop a machine learning model that predicts whether water is potable (safe to drink) or not potable based on physical and chemical properties.

## Dataset
- **Source:** [Kaggle Water Potability Dataset](https://www.kaggle.com/datasets/adityakadiwal/water-potability)  
- **File:** `data/water_potability.csv`  
- **Description:** Contains water quality parameters like pH, hardness, solids, chloramines, sulfate, conductivity, organic carbon, trihalomethanes, turbidity, and target `Potability` (1 = potable, 0 = not potable).

## Algorithm
1. Load dataset and examine structure.
2. Handle missing values (fill with median).
3. Separate features (`X`) and target (`y`).
4. Standardize features.
5. Split data into training (80%) and testing (20%) sets.
6. Train a **Random Forest Classifier**.
7. Predict on test set and evaluate:
   - Accuracy
   - Confusion Matrix
   - Classification Report (Precision, Recall, F1-Score)

## Program
```
from google.colab import files

# This will open a file chooser to upload your CSV file
uploaded = files.upload()
import pandas as pd

# The uploaded file will be in the current working directory
df = pd.read_csv('water_potability.csv')

# Check first few rows
df.head()
# Example: split data and train model
X = df.drop('Potability', axis=1)
y = df['Potability']

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

model = RandomForestClassifier(random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

accuracy = accuracy_score(y_test, y_pred)
print(f'✅ Accuracy: {accuracy*100:.2f}%')
give in github format
```
## Output

<img width="1272" height="275" alt="Screenshot 2025-10-25 142034" src="https://github.com/user-attachments/assets/fdb94f2f-5b7f-436f-a9cc-13f66f9ddaeb" />
<img width="907" height="70" alt="Screenshot 2025-10-25 141703" src="https://github.com/user-attachments/assets/bf394155-e97c-430a-8af5-144b6706b876" />


## Results
- Accuracy: ~69.05% (varies with dataset split and preprocessing)
