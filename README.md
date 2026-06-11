# Heavy Machinery Predictive Maintenance & Industrial IoT Analytics

This repository applies Advanced Analytics and Machine Learning to predict heavy equipment failures before they occur. By converting raw sensor telematics data into actionable business strategies, this project optimizes fleet uptime and transforms traditional calendar-based servicing into real-time condition-based maintenance.

## 📈 Business Problem
Unscheduled downtime in heavy machinery (such as mining trucks, excavators, and industrial components) leads to catastrophic financial losses and operational delays. The primary objective is to build a reliable predictive system that warns maintenance crews of imminent machine failures 24 hours in advance, ensuring workplace safety and cost reduction.

## 🛠️ Data Cleansing & Feature Engineering
*   **Data Standardisation**: Handled structural discrepancies by casting misclassified string formats (`str`) of critical telematics variables into high-precision decimal floats (`float64`).
*   **Feature Creation**: Developed a high-value domain-specific indicator called **`Temperature difference [K]`** (the mathematical delta between *Process Temperature* and *Air Temperature*) to effectively capture engine overheating patterns.

## 📊 Exploratory Data Analysis (EDA) Insights
Through correlation matrix analysis and statistical exploration, key physical behaviors of the machinery were successfully uncovered:
1.  **Inverse Mechanical Relationship (-0.88 Correlation)**: A strong negative correlation between `Rotational speed [rpm]` and `Torque [Nm]` confirms that peak mechanical stress occurs at high torque with lower RPMs.
2.  **Imbalanced Data Profile**: Revealed that machine failures constitute only **3.39%** (339 instances) of the entire operational dataset, establishing a classic real-world imbalanced classification problem.

## 🤖 Machine Learning Modeling & Evaluation
A **Random Forest Classifier** was trained to predict the `Machine failure` label. To combat severe class imbalance, the algorithm was tuned using balanced class weighting strategies.

*   **Overall Accuracy**: 98.3%
*   **Fault Detection Capability (Recall)**: **78.0%** — The AI successfully intercepts 78% of actual machine failures before a complete breakdown occurs.
*   **Alarm Precision**: 74.0% — Minimizes costly false alarms for field engineers.

## 💡 Key Drivers of Machinery Failure
Based on the trained AI model's Feature Importance extraction, the primary catalysts for hardware failure are:
1.  **Torque (36%)**: Excessive torsional load is the leading indicator of component degradation.
2.  **Rotational Speed & Tool Wear (22%-24%)**: Continuous high-speed friction and physical part degradation over time are secondary risk factors.
3.  **Engine Overheating Delta (9%)**: The engineered *Temperature Difference* metric proved to be a far superior predictor than tracking environment or process temperatures independently.

## 🚀 Strategic Business Recommendations
*   **Implement Overload Triggers**: Set up automated telemetry alerts on the machinery's dashboard when `Torque` exceeds critical thresholds for extended durations.
*   **Dynamic Maintenance Scheduling**: Pivot from strict calendar schedules to automated maintenance triggers when `Tool wear [min]` or cumulative `Temperature difference` benchmarks are breached.
