#To run the code the user requires tensorflow, numpy ,pandas and scikit as libraries and execute it by specifying the csv file in the format provided by NASDAQ site

After executing it the algorithm gives out a prediction of one day ahead into the future and one can analyse their knowledge on stocks. As stocks are a sensitive topic, any decision taken by you is guided by you alone, do not come at me if u lose money using this code or anything.This tool just analysizes past data and gives out a prediction, nothing more nothing less

#The dataset was taken from NASDAQ's website more info can be found here https://www.nasdaq.com/market-activity/quotes/historical

# 📈 Netflix Stock Price Prediction using LSTM

This project uses an **LSTM (Long Short-Term Memory)** model built with **Keras** and **TensorFlow** to predict Netflix stock prices based on historical data.

---

## 📄 Dataset
- File used: `Netflix_alltime.csv`
- Columns: `Date`, `Close/Last`, `Open`, `High`, `Low`, `Volume`
- Preprocessing:
  - Dates are reversed (oldest first).
  - Dollar signs (`$`) are removed.
  - Data is converted to numeric types.

---

## 🛠 Libraries Used

- `pandas`
- `numpy`
- `keras`
- `sklearn`
- `tensorflow`

---

## ⚙️ Preprocessing Steps

1. **Load and clean data**  
   - Remove dollar signs (`$`) from price columns.
   - Reverse the order of the dataset (oldest date first).

2. **Prepare time-series data**
   - Use a **window of 10 days** (`time_steps = 10`) to predict the next day's stock features.

3. **Split into train and test**
   - 80% training, 20% testing.

4. **Normalize**
   - MinMaxScaler is applied separately to input (`X`) and output (`y`).

---

## 🧠 Model Architecture

| Layer | Details |
|:------|:--------|
| 1 | `LSTM(128 units)` with `relu` activation |
| 2 | `Dense(128 units)` |
| 3 | `Dense(5 units)` (output layer for 5 features: Close, Open, High, Low, Volume) |

- **Loss Function**: Mean Squared Error (`mse`)
- **Optimizer**: Adam with a custom learning rate `0.001`
- **Epochs**: 200
- **Batch Size**: 32

---

## 🚀 Training Output

- **Final Test Loss**: `~0.0014`
- **Prediction Output** (example):
  ```
  Predicted: [[577, 3131773, 576, 587, 568]]
  ```

---

## 📈 Model Performance Graphs (optional)

If needed, you can plot:
- Loss over epochs
- Validation loss vs training loss

Example:
```python
import matplotlib.pyplot as plt

plt.plot(history.history['loss'], label='Training Loss')
plt.plot(history.history['val_loss'], label='Validation Loss')
plt.title('Model Loss Over Epochs')
plt.ylabel('Loss')
plt.xlabel('Epoch')
plt.legend()
plt.show()
```

---

## 📂 How to Run

1. Clone the repository.
2. Place your `Netflix_alltime.csv` in the working directory.
3. Install dependencies:
   ```bash
   pip install pandas numpy keras scikit-learn tensorflow
   ```
4. Run the script:
   ```bash
   python lstm_netflix_prediction.py
   ```


# 🌟 Future Improvements
- Add **Dropout** layers for regularization.
- Try **Bidirectional LSTM**.
- Use **multiple stocks** to predict Netflix.
- Predict **only 'Close'** prices instead of all 5 features if needed.

---

