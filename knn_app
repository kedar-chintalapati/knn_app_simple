import streamlit as st
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, classification_report
import pandas as pd

# Title of the app
st.title("K-Nearest Neighbors Classifier")

# Upload the dataset
uploaded_file = st.file_uploader("Upload a CSV file", type=["csv"])

# Sidebar for user input on KNN parameters
st.sidebar.header("Model Parameters")
k = st.sidebar.slider("Number of Neighbors (k)", min_value=1, max_value=20, value=5, step=1)
test_size = st.sidebar.slider("Test Size (%)", min_value=10, max_value=50, value=20, step=5) / 100

if uploaded_file:
    # Load dataset
    data = pd.read_csv(uploaded_file)
    st.write("Data Preview:")
    st.write(data.head())

    # Select features and target
    target = st.selectbox("Select the target column", data.columns)
    features = st.multiselect("Select feature columns", data.columns.drop(target))

    if features:
        X = data[features]
        y = data[target]

        # Split data
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=test_size, random_state=42)

        # Train the KNN model
        model = KNeighborsClassifier(n_neighbors=k)
        model.fit(X_train, y_train)

        # Make predictions and display results
        y_pred = model.predict(X_test)
        accuracy = accuracy_score(y_test, y_pred)
        st.write(f"Model Accuracy: {accuracy:.2f}")
        st.write("Classification Report:")
        st.text(classification_report(y_test, y_pred))
    else:
        st.warning("Please select at least one feature column.")
else:
    st.info("Please upload a CSV file to begin.")
