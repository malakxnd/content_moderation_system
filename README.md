# 🛡️ Comment Moderation System (Spam & Toxicity Detection)

An AI-powered content moderation system that detects spam and toxic comments in online communities.
This project combines machine learning and NLP to filter harmful content, while also exploring bias across race, religion, gender, and sexual orientation.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🚀 Highlights of My Work

* Built a **two-stage moderation system** (Spam + Toxicity).
* **Spam detection**: positive–unlabeled learning with Logistic Regression → **99% validation accuracy**.
* **Toxicity detection**: TF-IDF + Logistic Regression → **ROC AUC = 0.93**, **F1 = 0.65**.
* **Risk model**: combined spam & toxicity → **Final Accuracy = 0.91** on unseen data.
* Designed **custom rules** for caps ratio, URL count, repetition, and blacklist terms.
* Showcased **data-driven insights**: which groups (race, religion, orientation, gender) are most targeted by toxicity.
* Visualized patterns with **word clouds, probability distributions, and comment length analysis**.

---

## 🧠 Workflow

### 1. Data Preprocessing

* Lowercased all comments.
* Removed URLs, mentions, hashtags, HTML tags, emojis, numbers.
* Normalized repeated characters (e.g., `soooo → soo`).
* Removed stopwords (kept negations like *not*, *never*).
* Lemmatized words for normalization.

---

### 2. Spam Detection

* Started with **rule-based heuristics**:

  * `url_count`, `caps_ratio`, `emoji_count`, `special_char_count`, `char repetition`.
  * Regex for typical spam phrases (“free money”, “buy now”, etc.).
* Labeled positives using rules, then treated unlabeled as negatives with **positive–unlabeled learning**.
* **Model**: Logistic Regression + TF-IDF.
* **Validation Accuracy**: **0.99**.
* **Spam Probability Distribution** clearly separated spam (near 1.0) from clean text (near 0.0).

---

### 3. Toxicity Detection

* Defined a **toxic blacklist** (slurs, explicit content, violent terms).
* Added Jigsaw toxic attributes: `severe_toxicity`, `insult`, `threat`, etc.
* Preprocessed text with TF-IDF (100k vocab, uni- + bigrams).
* Tested models:

  * Naive Bayes → **AUC 0.77**
  * Linear SVM → **AUC 0.91**
  * Logistic Regression → **AUC 0.93** (**chosen**)
  * Random Forest → **AUC 0.81**
* Final Logistic Regression gave:

  * **Accuracy**: 0.91
  * **F1**: 0.65
  * **ROC AUC**: 0.93

---

### 4. Risk Assessment

* Combined spam & toxic models into a single **risk score**:

  $$
  Risk = 0.85 \times Toxicity + 0.15 \times Spam
  $$
* Tuned threshold with **precision-recall curves** → Best F1 at **0.5861**.
* On unseen dataset:

  * **Accuracy**: 0.91
  * **Precision**: 0.65
  * **Recall**: 0.65
  * **F1**: 0.65

---

## 📊 Data Insights (Visualization Titles)

<img width="1489" height="990" alt="image" src="https://github.com/user-attachments/assets/55e7f080-2fc6-474c-8764-3ea9ca899446" />
Insights:

Toxicity against "muslim" group spiked in specific months
"black" identity consistently receives high toxicity
---

<img width="566" height="547" alt="image" src="https://github.com/user-attachments/assets/1c59d2d6-11b0-436b-a42e-03c45b55ae12" />

Insight: there might be a class-imbalance

---

<img width="593" height="455" alt="image" src="https://github.com/user-attachments/assets/3173b890-16c2-464c-b95e-e107489f509d" />

insight => comment length both toxic and non-toxic looks almost same only

---

<img width="1104" height="288" alt="image" src="https://github.com/user-attachments/assets/ebe96e71-976a-4bcc-b977-a24a2a239dea" />

Insight => the most frequent words individually in positive and negative comments both have similar words like people, trump, think....

---

## 🛠️ Tech Stack

* **Python** (pandas, scikit-learn, matplotlib, regex, nltk)
* **Models**: Logistic Regression, Linear SVC, Naive Bayes, Random Forest
* **Methods**: TF-IDF, PU Learning, blacklist rules, precision-recall optimization

---

## 🎯 Why This Project Stands Out

* Designed to work with **huge datasets** without uploading the full data (efficient sampling).
* Balanced **rules + machine learning** for explainable moderation.
* Achieved **91% accuracy on unseen data**.
* Produced **real-world insights** into online harassment patterns.

🔥 This README is **tailored to your exact workflow** — every number and method reflects what you did.
You can now **insert your plots under the "Data Insights" section** to make it visually convincing.

👉 Do you also want me to write a **short recruiter-facing tagline at the top** (like one line that instantly sells it as “ML-powered moderation system with 91% accuracy on real-world data”)?
