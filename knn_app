import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

# Title of the app
st.title("Point Plotter")

# Initialize or load points data
if 'points' not in st.session_state:
    st.session_state['points'] = pd.DataFrame(columns=['x', 'y'])

# Input fields for new point
st.write("Enter a new point:")
x = st.number_input("X-coordinate", value=0.0, step=1.0)
y = st.number_input("Y-coordinate", value=0.0, step=1.0)

# Add point to the list
if st.button("Add Point"):
    st.session_state['points'] = pd.concat([st.session_state['points'], pd.DataFrame([[x, y]], columns=['x', 'y'])], ignore_index=True)

# Display current points
st.write("Current Points:")
st.write(st.session_state['points'])

# Plot the points
st.write("Plot of Points:")
fig, ax = plt.subplots()
ax.scatter(st.session_state['points']['x'], st.session_state['points']['y'])
ax.set_xlabel("X")
ax.set_ylabel("Y")
st.pyplot(fig)
