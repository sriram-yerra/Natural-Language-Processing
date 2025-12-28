## **Spam Classification Pipeline**

```text
Raw SMS text
   ↓
Text Cleaning & Preprocessing
   ↓
Corpus (cleaned sentences)
   ↓
Vectorization (BoW / TF-IDF)
   ↓
Train–Test Split
   ↓
Model Training (Naive Bayes)
   ↓
Prediction
   ↓
Evaluation (Accuracy + Classification Report)
 
 ---

 Raw Data
   ↓
Transformer (e.g., TF-IDF, Scaler)
   ↓
Features
   ↓
Estimator (e.g., Naive Bayes, RandomForest)
   ↓
Predictions

---

## 🌲 Why `RandomForestClassifier` Does Not Have `fit_transform()`

In scikit-learn, different components play different roles in a machine learning pipeline.  
Some are used to **transform data**, while others are used to **learn from data and make predictions**.

Understanding this explains why `RandomForestClassifier` does not implement `fit_transform()`.

---

## 🔄 Transformers vs Estimators (Models)

scikit-learn broadly categorizes tools into:

### 🧱 **Transformers — Change the data**

Transformers are used to convert raw data into a new feature representation.  
They learn parameters from the data and then apply a transformation.

They provide:
- **fit()** → learn from data  
- **transform()** → transform data  
- **fit_transform()** → fit + transform in one step  

**Examples:**
- CountVectorizer (text → word counts)  
- TfidfVectorizer (text → TF-IDF features)  
- StandardScaler (scale features)  
- PCA (dimensionality reduction)  

```python
X = TfidfVectorizer().fit_transform(corpus)

### 🤖 **Estimators / Models — Learn & Predict**

Estimators (also called models) are used to learn a mapping from input features **X** to output labels **y**.  
Their role is to **make predictions**, not to change the data representation.

They provide:
- **fit()** → train the model  
- **predict()** → predict labels for new data  

They do **not** provide:
- **transform()**  
- **fit_transform()**

**Examples:**
- MultinomialNB  
- RandomForestClassifier  
- LogisticRegression  
- SVC  

```python
from sklearn.ensemble import RandomForestClassifier

clf = RandomForestClassifier()
clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)


