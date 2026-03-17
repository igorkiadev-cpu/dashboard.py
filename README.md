import streamlit as st
import pandas as pd
import numpy as np
import plotly.express as px

st.title("ROV Mission Intelligence Platform")

st.write("Interactive dashboard for analyzing ROV mission data.")

# Generate simulated mission data
points = 100

time = np.arange(points)
depth = np.abs(np.cumsum(np.random.normal(0.5, 0.2, points)))
x = np.cumsum(np.random.normal(0.3, 0.1, points))
y = np.cumsum(np.random.normal(0.3, 0.1, points))

df = pd.DataFrame({
    "Time": time,
    "Depth": depth,
    "X": x,
    "Y": y
})

st.subheader("Mission Depth Profile")

fig_depth = px.line(df, x="Time", y="Depth")

st.plotly_chart(fig_depth)

st.subheader("ROV Mission Path")

fig_path = px.scatter(df, x="X", y="Y")

st.plotly_chart(fig_path)

st.subheader("Mission Data")

st.dataframe(df)
