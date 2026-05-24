# SMS Confirmation Requirements

## Overview

The TeaRoutePay system aims to improve transparency and communication between the tea collection business and farmers through SMS notifications.

Currently, farmers depend on manual communication methods to verify tea collection records. The proposed SMS notification feature will notify farmers after collection data is synchronized with the main system.

This document identifies SMS notification scenarios, required message content, trigger points, tea leaf deduction handling, and failed SMS delivery requirements.

---

# Objectives

The SMS notification system is intended to:

- Improve transparency in tea collection records
- Notify farmers about synchronized tea collection records
- Reduce unnecessary office inquiries
- Improve farmer trust in the collection process
- Provide confirmation of final tea leaf net weight

---

# SMS Confirmation Scenarios

The system should support SMS notifications in the following scenarios.

| Scenario | Description |
|---|---|
| Tea Collection Confirmation | Notify farmers after tea collection data is synchronized to the main system |
| Net Weight Confirmation | Inform farmers about final net tea leaf weight after deductions |
| Collection Record Confirmation | Confirm that tea collection details are successfully stored |
| Failed SMS Notification | Inform office staff if SMS delivery fails |

---

# SMS Trigger Points

SMS notifications should be triggered only after synchronization with the main system.

## 1. Tea Collection Synchronization
After tea leaves are collected and recorded through the mobile application, the data is synchronized with the main system. SMS notifications should only be sent after successful synchronization.

## 2. Final Net Weight Calculation
SMS should be triggered after calculating the final net tea leaf weight following applicable deductions.

---

# Tea Leaf Weight Deduction Rules

The system should support tea leaf weight deductions before calculating the final net weight.

## 1. Rope Sack Deduction
If the tea sack is identified as a rope sack, 1 kilogram should be deducted from that sack.

## 2. Water Content Deduction
If excess water is detected in tea leaves, 1 kilogram should be deducted from that sack.

## 3. Final Net Weight
The final tea leaf weight after all deductions should be calculated and stored in the system.

This final net weight should be included in the SMS notification sent to the farmer.

---

# Required SMS Message Content

The SMS notification should contain important collection information.

## Required Information

- Farmer name
- Collection date
- Final net tea leaf weight
- Confirmation message
- Business/company name

---

# Example SMS Messages

## Example 1 – Tea Collection Confirmation

```text
Dear Farmer,
Your tea collection has been successfully recorded.
Final Net Weight: 48 Kg
- TeaRoutePay