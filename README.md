<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
</head>
<body style="font-family: Arial, sans-serif; line-height: 1.6; margin: 20px; max-width: 800px;">

  <h1>💬 Sentiment Analysis on Book Reviews</h1>
  <p>
    This Jupyter-based machine learning project classifies Amazon book reviews as <strong>Positive</strong> or <strong>Negative</strong> based on review content.
    It applies different machine learning models and vectorization strategies to improve sentiment classification accuracy.
  </p>

  <h2>✨ Features</h2>
  <ul>
    <li><strong>Sentiment Classification:</strong> Predicts sentiment as either POSITIVE or NEGATIVE.</li>
    <li><strong>Balanced Dataset:</strong> Adjusts the dataset to contain an equal number of positive and negative reviews to avoid bias.</li>
    <li><strong>Improved Vectorization:</strong> Replaced <code>CountVectorizer</code> with <code>TfidfVectorizer</code> for better handling of important terms.</li>
    <li><strong>Multiple Classifiers:</strong> Compares performance of SVM, Logistic Regression, Decision Tree, and Naive Bayes.</li>
    <li><strong>Evaluation Metrics:</strong> Includes Accuracy and F1 Score to evaluate model effectiveness.</li>
  </ul>

  <h2>📘 Dataset Details</h2>
  <p>
    Initially, the project used the <code>Books_small_1000.json</code> file, but the dataset was heavily skewed toward positive reviews,
    resulting in poor performance for detecting negative sentiment. To address this, we switched to using
    <code>Books_small_10000.json</code>, which contains 10,000 reviews. Even then, neutral reviews were sparse and not statistically meaningful,
    so <strong>only POSITIVE and NEGATIVE reviews were retained</strong>.
  </p>
  <p>
    The dataset was manually balanced by selecting an equal number of negative and positive reviews. Neutral reviews were excluded from both training and evaluation.
  </p>

  <h2>🧪 Machine Learning Details</h2>
  <ul>
    <li><strong>Data:</strong> Amazon Book Reviews (<code>Books_small_10000.json</code>)</li>
    <li><strong>Preprocessing:</strong>
      <ul>
        <li>Text reviews converted to objects with sentiment labels.</li>
        <li>Sentiments labeled as:
          <ul>
            <li>1–2 stars → NEGATIVE</li>
            <li>4–5 stars → POSITIVE</li>
            <li>3 stars (NEUTRAL) → Ignored</li>
          </ul>
        </li>
        <li>Dataset balanced: equal number of POSITIVE and NEGATIVE reviews</li>
      </ul>
    </li>
    <li><strong>Vectorization:</strong> Used <code>TfidfVectorizer</code> to better highlight distinctive words over common ones.</li>
    <li><strong>Models Used:</strong>
      <ul>
        <li>Support Vector Machine (SVM)</li>
        <li>Logistic Regression</li>
        <li>Decision Tree</li>
        <li>Naive Bayes</li>
      </ul>
    </li>
  </ul>

  <h2>📊 Model Performance</h2>
  <table border="1" cellpadding="8" cellspacing="0">
    <thead>
      <tr>
        <th>Model</th>
        <th>Accuracy</th>
        <th>F1 Score (POS, NEG)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>SVM (linear)</td>
        <td>0.81</td>
        <td>(0.81, 0.81)</td>
      </tr>
      <tr>
        <td>Logistic Regression</td>
        <td>0.80</td>
        <td>(0.80, 0.80)</td>
      </tr>
      <tr>
        <td>Naive Bayes</td>
        <td>0.66</td>
        <td>(0.66, 0.67)</td>
      </tr>
      <tr>
        <td>Decision Tree</td>
        <td>0.65</td>
        <td>(0.64, 0.66)</td>
      </tr>
    </tbody>
  </table>

  <h2>🛠️ Model Optimization & Deployment</h2>
  <ul>
    <li><strong>Model Tuning:</strong> Grid Search was used to optimize the SVM model. The best configuration was found with <code>C=4</code> and <code>kernel='linear'</code>.</li>
    <li><strong>Model Saving:</strong> The trained model was saved using <code>pickle</code> for future prediction tasks.</li>
    <li><strong>Testing:</strong> Predictions were made on new review samples to verify the model's effectiveness.</li>
  </ul>

  <h2>📁 Project Structure</h2>
  <pre>
Sentiment_Analysis/
│
├── data/
│   └── Books_small_10000.json       # Review dataset
│
├── models/
│   └── sentiment_classifier.pkl     # Trained and saved SVM model
│
├── main.ipynb                       # Main notebook for data prep, training, and evaluation
  </pre>

  <h2>⚠️ Disclaimer</h2>
  <p>
    This project is for educational purposes only. It is not intended for use in real-world production environments without further validation,
    error handling, and ethical considerations. Neutral sentiment is excluded due to insufficient representation in the dataset.
  </p>

</body>
</html>
