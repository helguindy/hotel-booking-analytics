# 🧩 Setup

1. Go to **Kaggle → Code → New Notebook → File → Link to GitHub**.  
2. On Kaggle, click **File → Import Notebook**.  
3. Choose **GitHub** and search for `helguindy`.  
4. Open the repo **hotel-booking-analytics**.  
5. Go to the `notebooks/` folder and select your own notebook.  
6. Work only inside your notebook.  
7. When done, click **Save Version → Save & Run All**.  
8. Make sure **Save to GitHub (main branch)** is selected.  
9. Kaggle will automatically push your changes to GitHub.  

---

# 📂 Uploading the Dataset on Kaggle

1. On Kaggle, open your notebook.  
2. On the **right-hand side panel**, click **Add Data → Upload → New Dataset**.  
3. Click **Browse Files**.  
4. Go to the folder where you cloned the project:  
   `hotel-booking-analytics/data/`  
5. Select the three CSV files at once:  
   - `hotels.csv`  
   - `reviews.csv`  
   - `users.csv`  
6. When creating the dataset, name it exactly **`HotelDataset`** (important for consistency).  
7. Click **Create** to upload the dataset.  
8. Once uploaded, it will appear in the **Data** section on the right.  

---

# 🏨 Hotel Booking Analytics – Milestone 1 Workflow

## 1️⃣ Data Cleaning

**Goal:** Prepare a clean dataset for analysis and modeling.

1.  **Load the datasets**
    ```python
    import pandas as pd

    hotels = pd.read_csv("/kaggle/input/hoteldataset/hotels.csv")
    reviews = pd.read_csv("/kaggle/input/hoteldataset/reviews.csv")
    users = pd.read_csv("/kaggle/input/hoteldataset/users.csv")
    ```
2.  **Check for missing values**
    ```python
    hotels.isnull().sum()
    reviews.isnull().sum()
    users.isnull().sum()
    ```
3.  **Handle Missing Values**

4.  **Check for duplicates**

5.  **Remove unnecessary columns**
  
6.  **Merge datasets**

7.  **Add new columns**
    * `country_group` (map user countries to groups, e.g., USA → North_America).
8.  **Save cleaned dataset**
    ```python
    merged_df.to_csv("cleaned_hotel_data.csv", index=False)
    ```

---

## 2️⃣ Data-Engineering Questions

**Goal:** Explore and visualize the data to answer analysis questions.


1.  **Q1: Best city per traveler type**
    * Group by `traveller_type` and `city`.
    * Calculate average `score_overall` per group.
    * Sort and pick the top city for each traveler type.
    * Create a bar chart or table showing results.
      
2.  **Q2: Top 3 countries by value-for-money per age group**
    * Group by `age_group` and `country`.
    * Calculate average `score_value_for_money`.
    * Sort and pick top 3 countries per age group.
    * Visualize results (bar chart or line chart).


---

## 3️⃣ Prepare Dataset for Training

**Goal:** Prepare the dataset for predictive modeling.

1.  **Identify features to use:**

2.  **Convert categorical features to numbers:**

3.  **Prepare X (features) and y (target `country_group`)**

4.  **Split data into training/testing sets:**
    ```python
    from sklearn.model_selection import train_test_split

    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
    ```

---

## 4️⃣ Predictive Modeling

**Goal:** Build a model to predict `country_group`.

**Subtasks:**

1.  **Train a classifier** (RandomForest, Decision Tree, or shallow neural network)
    ```python
    from sklearn.ensemble import RandomForestClassifier

    model = RandomForestClassifier()
    model.fit(X_train, y_train)
    ```
2.  **Make predictions and evaluate:**
    ```python
    from sklearn.metrics import classification_report

    preds = model.predict(X_test)
    print(classification_report(y_test, preds))
    ```
3.  **Metrics to report:**
    * Accuracy
    * Precision
    * Recall
    * F1-score

---

## 5️⃣ Explainable AI 

* After you make a model to predict the country group, you might wonder: “Which features made the model decide this?”
* XAI tools like **SHAP** and **LIME** show you how important each feature is for the prediction.
* ✅ **It helps you understand the model’s “thinking” instead of it being a black box.**

---

## 6️⃣ Inference Function

* This is a function that takes new input data (like a new user’s age, gender, traveler type, review scores) and tells you the predicted country group.
* It’s like a **shortcut**, you don’t have to rerun the whole model every time you want a new prediction.
