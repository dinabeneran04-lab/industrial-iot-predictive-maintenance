# 🚜 Heavy Machinery Predictive Maintenance & Industrial IoT Analytics

[![Tableau](https://shields.io)](https://public.tableau.com/app/profile/dina.rahma.wita/vizzes)

This repository applies Advanced Analytics and Machine Learning to predict heavy equipment failures before they occur. By converting raw sensor telematics data into actionable business strategies, this project optimizes fleet uptime and transforms traditional calendar-based servicing into real-time condition-based maintenance.

## 📈 Business Problem
Unscheduled downtime in heavy machinery (such as mining trucks, excavators, and industrial components) leads to catastrophic financial losses, operational delays, and safety hazards. The primary objective of this project is to build a reliable predictive system that warns maintenance crews of imminent machine failures 24 hours in advance, ensuring workplace safety and optimal cost reduction.

## 🔗 Live Interactive Dashboard
You can explore and interact with the full telemetry monitoring dashboard built for field engineers here: 
👉 **[Tableau Public Dashboard Link](https://public.tableau.com/app/profile/dina.rahma.wita/vizzes)**

## 🛠️ Data Cleansing & Feature Engineering
*   **Data Quality Alignment**: Handled structural discrepancies by casting misclassified string formats (`str`) of critical telematics variables (Torque, Air/Process Temperature) into high-precision decimal floats (`float64`) using Python Regex to make the data digestible for machine learning algorithms.
*   **Advanced Feature Creation**: Developed a high-value, domain-specific indicator called **`Temperature difference [K]`** (the mathematical delta between *Process Temperature* and *Air Temperature*) to effectively capture engine overheating patterns.

## 📊 Exploratory Data Analysis (EDA) Insights
Through correlation matrix analysis and statistical exploration, key physical behaviors of the machinery were successfully uncovered:
1.  **Inverse Mechanical Relationship (-0.88 Correlation)**: A strong negative correlation between `Rotational speed [rpm]` and `Torque [Nm]` confirms the engineering law that peak mechanical stress occurs at high torque with lower operating RPMs.
2.  **Imbalanced Data Profile**: Revealed that machine failures constitute only **3.39%** (339 instances) of the entire 10,000 operational dataset, establishing a classic real-world imbalanced classification problem.

## 🤖 Machine Learning Modeling & Evaluation
A **Random Forest Classifier** was trained to predict the `Machine failure` label. To combat the severe class imbalance, the algorithm was optimized using balanced class weighting strategies (`class_weight='balanced'`).

*   **Overall Accuracy**: 98.3% — High overall precision in distinguishing machinery states.
*   **Fault Detection Capability (Recall)**: **78.0%** — The AI successfully intercepts 78% of actual machine failures 24 hours before a complete breakdown occurs.
*   **Alarm Precision**: 74.0% — Minimizes costly false alarms and unnecessary maintenance pull-outs for field engineers.

## 💡 Key Drivers & Root Cause Analysis
Based on the trained AI model's Feature Importance extraction and Tableau multidimensional analytics, the primary catalysts for hardware failure are:
1.  **Torque (36%)**: Excessive torsional load is the leading indicator of immediate mechanical failure.
2.  **Rotational Speed & Tool Wear (22%-24%)**: Continuous friction and physical part degradation over time act as secondary risk factors.
3.  **Engine Overheating Delta (9%)**: The engineered *Temperature Difference* metric proved to be a far superior predictor than tracking environment or process temperatures independently.
4.  **Failure Mode Breakdown**: Out of 5 failure tracks, **Heat Dissipation Failure (HDF)** was uncovered as the absolute leading root cause for machinery breakdown (**115 cases**), closely followed by Overstrain Failure (OSF) with 98 cases.

## 🚀 Strategic Business Recommendations
*   **Implement Overload Triggers**: Set up automated telemetry alerts on the machinery's dashboard when `Torque` spikes into the upper-bound risk zone at low RPMs for extended durations.
*   **Dynamic Maintenance Scheduling**: Pivot from strict calendar schedules to automated maintenance tickets once a machine's cumulative `Tool wear` hits the critical benchmark threshold of **140 minutes** or when the engineered `Temperature difference` breaches safety margins.
