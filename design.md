# NeuroPrep AI – System Design Document

## 1. System Overview

NeuroPrep AI is a cloud-native AI-driven Cognitive Performance Optimization system built using AWS services. 

The system analyzes mock test behavioral data and applies Large Language Model (LLM) reasoning to detect cognitive fatigue, stress patterns, and strategic inefficiencies.

Unlike traditional mock platforms, NeuroPrep AI evaluates *behavioral intelligence*, not just academic scores.

---

## 2. High-Level Architecture

       User (React Web Application)
               ↓
        Amazon API Gateway
               ↓
     AWS Lambda (Behavior Processing Layer)
               ↓
    Amazon Bedrock (LLM Cognitive Engine)
               ↓
    DynamoDB (User Cognitive Profiles)
               ↓
     Amazon S3 (Mock Test Data Storage)


## 3. Detailed Data Flow

1. User completes a mock test.
2. Raw attempt data (timestamps, question difficulty, correctness) stored in S3.
3. Lambda processes raw data and extracts structured behavioral metrics:
   - Avg time per difficulty
   - Accuracy drift over time
   - Attempt order pattern
   - Guess probability score
4. Structured JSON payload sent to Amazon Bedrock.
5. LLM performs contextual behavioral reasoning.
6. LLM outputs cognitive insights in structured format.
7. Output validated and stored in DynamoDB.
8. Dashboard displays cognitive intelligence metrics.

---

## 4. AI Workflow Design

### Step 1: Behavioral Metric Extraction
Lambda converts raw logs into structured performance vectors.

### Step 2: Prompt Engineering Strategy

System Prompt:
"You are an AI Cognitive Intelligence Coach specializing in exam behavioral analysis."

Input format:
{
  "avg_time_easy": value,
  "avg_time_medium": value,
  "accuracy_trend": [...],
  "difficulty_sequence": [...],
  "error_clusters": [...]
}

Few-shot examples guide:
- Fatigue detection
- Strategic inefficiency identification
- Risk-taking behavior analysis

### Step 3: LLM Cognitive Reasoning

Amazon Bedrock analyzes:
- Sequential performance degradation
- Cognitive load tolerance
- Strategy discipline consistency

### Step 4: Insight Generation

Outputs:
- Focus Stability Index (0–100)
- Fatigue Onset Threshold (minutes)
- Strategic Discipline Score
- Personalized Strategy Recommendations
- Score Prediction Range

---

## 5. Scalability & Performance

- Fully serverless architecture
- Auto-scaling Lambda functions
- DynamoDB adaptive capacity
- S3 optimized storage lifecycle

---

## 6. Security & Responsible AI

- No biometric or sensitive health data collected
- End-to-end encryption
- AI outputs reviewed via validation logic
- Transparent explanation of cognitive scores

---

## 7. Future Roadmap

- Mobile Application
- Coaching Institute Dashboard
- Multi-language Support
- Integration with national exam ecosystems


