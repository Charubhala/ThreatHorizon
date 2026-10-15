# ThreatHorizon — System Requirements

## 1. Purpose

This document defines the proposed functional and non-functional requirements for ThreatHorizon, a predictive cybersecurity architecture designed to forecast emerging threats, assess attack risk, and support bounded automated responses.

**Current status:** Design and documentation. Requirements describe intended capabilities and remain subject to implementation and testing.

## 2. Functional Requirements

### FR-01: Network Telemetry Collection
The system shall accept available network packets, flows, logs, and telemetry from configured monitoring sources.

### FR-02: Signal Conditioning
The system shall support protocol parsing, flow/session aggregation, data cleaning, deduplication, and normalization.

### FR-03: Feature Extraction
The system shall derive statistical, temporal, behavioral, graph-based, and contextual features from processed telemetry.

### FR-04: Temporal Analysis
The system shall support sliding or tumbling time windows for organizing observations into time-series feature streams.

### FR-05: Anomaly Detection
The system shall analyze available features to identify deviations from expected network or behavioral patterns.

### FR-06: Temporal Forecasting
The system shall support analysis of trends and potential future behavioral patterns.

### FR-07: Attack Classification
The system shall support classification of suspected or emerging attack categories.

### FR-08: Threat Intelligence Matching
The system shall support comparison of relevant observations with configured signatures and available threat intelligence.

### FR-09: Graph Analytics
The system shall support analysis of relationships among relevant hosts, entities, sessions, or communication patterns.

### FR-10: Drift Detection
The system shall identify relevant behavioral or data-distribution changes that may affect analysis reliability.

### FR-11: Signal Fusion
The system shall combine outputs from multiple analytical engines into a unified threat assessment.

### FR-12: Attack Risk Forecasting
The system shall aim to estimate attack probability, likely attack type, potential attack stage, expected timing, and forecast uncertainty.

### FR-13: Risk Assessment
The system shall map forecast evidence to configured LOW, MEDIUM, HIGH, and CRITICAL risk levels.

### FR-14: Risk-Based Alerts
The system shall support alerts, monitoring, analyst review, and escalation according to configured policies.

### FR-15: Bounded Automated Response
The system shall support configured and authorized mitigation actions, such as rate limiting or firewall/SDN controls, subject to defined safeguards.

### FR-16: Rollback
The system shall support rollback of eligible automated changes and record the corresponding action.

### FR-17: Analyst Feedback
The system shall support analyst actions such as accepting, rejecting, modifying, or escalating a finding.

### FR-18: Continual Learning
The system shall support a controlled model-improvement process involving validated feedback, replay, retraining, and evaluation before model promotion.

### FR-19: Explainability and Audit
The system shall record relevant forecast explanations, decision traces, response logs, and model-version information.

### FR-20: Presentation
The system shall support presentation of risk timelines, alerts, forecast explanations, and recommended actions.

## 3. Non-Functional Requirements

### NFR-01: Timeliness
The architecture should process telemetry and generate useful warnings quickly enough to support preventive action. Performance targets must be established through testing.

### NFR-02: Forecast Quality
The system should be evaluated for precision, recall, false-positive rates, false-negative rates, calibration, and useful forecast lead time.

### NFR-03: Reliability
The system should handle invalid, duplicated, incomplete, or delayed telemetry without silently corrupting downstream analysis.

### NFR-04: Security
The implementation should protect credentials, sensitive telemetry, model artifacts, feedback data, and audit records through appropriate access controls.

### NFR-05: Explainability
Important forecasts and security actions should have traceable supporting evidence and recorded decision context.

### NFR-06: Controlled Automation
Automated actions should follow explicit policies, enforce defined limits, and support rollback where technically possible.

### NFR-07: Model Safety
Model updates should undergo validation and shadow testing before deployment, with safeguards against performance degradation and catastrophic forgetting.

### NFR-08: Maintainability
The architecture should use clearly defined components and interfaces so that analytical engines and enforcement mechanisms can be developed and tested independently.

### NFR-09: Scalability
The implementation should be designed to handle the expected telemetry volume and growth in monitored hosts. Capacity targets must be established through testing.

### NFR-10: Auditability
Relevant decisions, model versions, and response actions should be recorded to support investigation and evaluation.

## 4. Constraints and Assumptions

- Available telemetry determines which features and analytical engines can operate.
- Forecast accuracy depends on data quality, representative evaluation data, and the selected models.
- Risk thresholds and response policies must be calibrated and validated.
- Automated enforcement requires integration with appropriate network or security controls.
- Analyst feedback must be reviewed and validated before being used for model updates.
- Forecasts are estimates and should not be treated as certainty.

## 5. Acceptance Criteria

The following criteria should be evaluated when corresponding capabilities are implemented:

1. Telemetry can be processed into the required structured features.
2. Analytical engine outputs can be combined into a unified assessment.
3. Forecasts include probability or risk estimates and uncertainty information where supported.
4. Risk levels map to documented policies and intended actions.
5. Automated actions respect configured boundaries and rollback rules.
6. Decisions and response outcomes can be traced through audit records.
7. Model updates are evaluated before deployment.
8. Performance is measured against defined detection, calibration, latency, and lead-time targets.

## 6. Development Status

These requirements describe the proposed ThreatHorizon design. Implementation, integration, and acceptance testing remain future development activities.
