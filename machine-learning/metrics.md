# 📊 Classification Metrics Cheat Sheet

This guide covers key metrics used to evaluate classification models. Each metric includes its **definition**, **formula**, **interpretation**, and **when to use** it.

---

## ✅ Accuracy

- **Definition**: Proportion of correct predictions among all predictions.
- **Formula**:  
  Accuracy = (TP + TN) / (TP + TN + FP + FN)
- **Interpretation**: Measures overall correctness.
- **When to Use**: When classes are **balanced** and errors are equally costly.

---

## 🎯 Precision (Positive Predictive Value)

- **Definition**: Proportion of true positives among all predicted positives.
- **Formula**:  
  Precision = TP / (TP + FP)
- **Interpretation**: Of all predicted positives, how many are correct.
- **When to Use**: When **false positives** are costly (e.g., spam filters).
- **When to Prioritize Precision**:
    - **Goal**: Minimize false positives (be sure when you say "positive")
        1. Email Spam Detection: Avoid marking legitimate emails as spam.
        2. Loan Approval System: Only approve applicants who are truly creditworthy.
        3. Fraud Detection Alert: Avoid flagging normal transactions as fraud (to reduce customer complaints).
        4. Autonomous Driving Pedestrian Detection: Be certain before applying brakes on detecting a human to avoid unnecessary stops.
        5. Cancer Screening Tool in Mass Populations: If used as a second-step screening (after high recall first-step), we want only truly positive cases flagged.
---

## 🔍 Recall (Sensitivity / True Positive Rate)

- **Definition**: Proportion of actual positives that were correctly predicted.
- **Formula**:  
  Recall = TP / (TP + FN)
- **Interpretation**: Of all actual positives, how many were caught.
- **When to Use**: When **false negatives** are costly (e.g., disease detection).

- **When to Prioritize Recall**:

    - **Goal:** Minimize false negatives (catch every possible positive case)

        1. COVID-19 Testing: Detect every infected person, even at the cost of some false alarms.
        2. Intrusion Detection in Security Systems: Better to catch all possible attacks, even if some are false positives.
        3. Fire Alarm System: Trigger on all potential fire signs—even if it sometimes goes off unnecessarily.
        4. Medical Diagnosis (e.g., Tuberculosis, Cancer): Catch every patient with disease, even if some healthy people get flagged.
        5. Criminal Record Check for High-Risk Roles (e.g., childcare): Better to flag questionable cases than miss a real threat.
---

## ⚖️ F1 Score

- **Definition**: Harmonic mean of precision and recall.
- **Formula**:  
  F1 = 2 * (Precision * Recall) / (Precision + Recall)
- **Interpretation**: Balance between precision and recall.
- **When to Use**: When both false positives and false negatives matter, especially with **imbalanced classes**.

---

## 📉 Specificity (True Negative Rate)

- **Definition**: Proportion of actual negatives correctly identified.
- **Formula**:  
  Specificity = TN / (TN + FP)
- **Interpretation**: Of all true negatives, how many were correctly predicted.
- **When to Use**: To measure how well negatives are detected.

---

## 📊 ROC AUC (Receiver Operating Characteristic - Area Under Curve)

- **Definition**: Area under the ROC curve (TPR vs FPR across thresholds).
- **Formula**:  
  Computed using roc_auc_score(y_true, y_prob)
- **Interpretation**: 1.0 = perfect, 0.5 = random.
- **When to Use**: To evaluate **ranking quality** of classifier, especially on **balanced datasets**.

---

## 📈 PR AUC (Precision-Recall Area Under Curve)

- **Definition**: Area under the precision-recall curve.
- **Formula**:  
  Computed using precision_recall_curve and area under it.
- **Interpretation**: Emphasizes performance on **positive class**.
- **When to Use**: When working with **highly imbalanced datasets**.

---

## 📦 Confusion Matrix

- **Definition**: Table of actual vs predicted labels.
- **Structure**:

|                         | Predicted Positive | Predicted Negative |
|-------------------------|--------------------|--------------------|
| **Actual Positive**     | True Positive (TP) | False Negative (FN)|
| **Actual Negative**     | False Positive (FP)| True Negative (TN) |


- **Interpretation**: Core metric that feeds into all others.
- **When to Use**: To understand types of model errors clearly.

---

> ✅ Choose metrics based on **problem context**, **class balance**, and **consequences of errors**.
