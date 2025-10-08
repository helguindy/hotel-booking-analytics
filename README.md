# 🧩 Setup

1. Go to **Kaggle → Code → New Notebook → File → Link to GitHub**.  
2. On Kaggle, click **File → Import Notebook**.  
3. Choose **GitHub** and search for `HLGindy`.  
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
9. Load the data in your notebook using:

   ```python
   import pandas as pd

   hotels = pd.read_csv("/kaggle/input/hoteldataset/hotels.csv")
   reviews = pd.read_csv("/kaggle/input/hoteldataset/reviews.csv")
   users = pd.read_csv("/kaggle/input/hoteldataset/users.csv")
