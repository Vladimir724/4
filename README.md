import kagglehub
import pandas as pd
import os

path = kagglehub.dataset_download("gyanashish/healthcare-diabetes")
filename = os.listdir(path)[0]
ds = pd.read_csv(os.path.join(path, filename))

print(ds.isnull().sum())
print((ds == 0).sum())
print(ds.dtypes)

group_1 = ds[ds['Outcome'] == 1]
group_0 = ds[ds['Outcome'] == 0]

mean_bp_1 = group_1['BloodPressure'].mean()
mean_bp_0 = group_0['BloodPressure'].mean()

print(f"Среднее давление при диабете: {mean_bp_1}")
print(f"Среднее давление без диабета: {mean_bp_0}")
