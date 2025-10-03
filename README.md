# Data-analyst-noosh
Be expert
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

# Load dataset
data = pd.read_csv("salary_age.csv")  # CSV file with Age and Salary columns
data['Age'] = data['Age'].fillna(data['Age'].mean())

# Split features and target
X = data[['Age']]
y = data['Salary']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = LinearRegression()
model.fit(X_train, y_train)

# Interactive prediction
while True:
    try:
        user_age = float(input("Enter your age (negative to exit): "))
        if user_age < 0:
            print("Goodbye!")
            break
        predicted_salary = model.predict([[user_age]])[0]
        print(f"Predicted salary for age {user_age:.1f}: {predicted_salary:.2f}")
    except ValueError:
        print("Please enter a valid number.")
