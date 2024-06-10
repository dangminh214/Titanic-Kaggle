# Title: Titanic Problem and Prediction in Kaggle 

## Check input-dataset 
```ruby
train_data.isna().sum()
```

## Data Process: 
Drop unnecessary columns from the dataset 
```ruby
train_data.drop(columns=['Age'], inplace=True)
train_data.drop(columns=['Cabin'], inplace=True)
train_data.dropna(subset=['Embarked'], inplace=True)
```

### Create y - predicted value 
```ruby
y = train_data["Survived"]
```
### Choose features to train 
```ruby
features = ['PassengerId', 'Pclass', 'SibSp', 'Parch', 'Fare']
X = train_data[features]
```

### Predict data 
```ruby
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier()
model.fit(X,y)
test = pd.read_csv('dataset/test.csv')
test_features = ['PassengerId', 'Pclass', 'SibSp', 'Parch', 'Fare']
predict_data = test[test_features]
print(predict_data)
print(predict_data.isna().sum())
predict_data = predict_data.fillna(predict_data['Fare'].mean())
#predict_data.describe()
res = model.predict(predict_data)
```
