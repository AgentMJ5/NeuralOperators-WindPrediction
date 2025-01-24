# Neural Operators for Wind Speed Prediction

This project demonstrates the use of Fourier Neural Operators (FNOs) to upscale coarse-resolution wind speed data to fine-resolution predictions. The methodology utilizes meteorological data from the ERA5 dataset and evaluates the effectiveness of neural operators in predicting high-resolution wind speed dynamics.

---

## **Project Overview**
The objective of this project is to map coarse-resolution wind speed data to a fine-resolution grid using Neural Operators. By leveraging the Fourier Neural Operator (FNO) architecture, we can efficiently learn mappings in function space, enabling high-resolution predictions without the need for expensive traditional numerical simulations.

### **Applications**
- **Renewable Energy**: Fine-resolution wind speed predictions can optimize wind farm siting and power generation.
- **Climate Modeling**: Enhances spatial accuracy in regional climate predictions.
- **Disaster Management**: Provides better wind dynamics predictions for extreme weather events.

---

## **Dataset Description**
The project uses meteorological data from the **ERA5 dataset**, provided by the European Centre for Medium-Range Weather Forecasts (ECMWF). The variables used are:

### **Variables**:
- **u10**: Eastward wind component at 10 meters.
- **v10**: Northward wind component at 10 meters.
- Derived Variable: **Wind Speed** (calculated as \( \sqrt{u10^2 + v10^2} \))

### **Data Used**:
1. **Training Data**:
   - January 2024 wind speed data for the Indian region.
2. **Testing Data**:
   - January 2025 wind speed data for the same region.

### **Geographical Region**:
The dataset focuses on the Indian subcontinent:
- **Latitude Range**: 8.0°N to 37.5°N
- **Longitude Range**: 68.0°E to 97.0°E

This region includes diverse terrains, making it an ideal testbed for wind speed modeling and prediction.

---

## **Methodology**

### **1. Data Preprocessing**
1. **Calculate Wind Speed**:
   - Derived from `u10` and `v10` components.
2. **Spatial Downscaling**:
   - Coarse-resolution grid created using a factor of 4 (e.g., \(30 \times 30\) grid).
3. **Fine-Resolution Grid**:
   - Original high-resolution wind speed data (e.g., \(119 \times 117\) grid).

### **2. Model Architecture**
The Fourier Neural Operator (FNO) maps coarse inputs to fine outputs. Key components include:
- **Input Layer**:
  - Maps single-channel input (coarse wind speed) to higher-dimensional features.
- **Fourier Layers**:
  - Encodes global spatial patterns using spectral decomposition.
- **Upsampling Layer**:
  - Outputs predictions at the desired fine resolution.

### **3. Training**
- **Loss Function**: Mean Squared Error (MSE)
- **Optimizer**: Adam optimizer
- **Training Epochs**: 50

---

## **Results**

### **Performance Metrics**
- **Training Data MAE**: \(0.4428\)
- **Testing Data MAE (January 2025)**: \(0.5568\)

### **Visualizations**
1. **Ground Truth vs. Predictions**:
   - Predicted fine-resolution wind speed closely matches the ground truth.
2. **Error Map**:
   - Highlights regions with higher discrepancies, with errors ranging from \(-3\) to \(+2\) m/s.

---

## **How to Use**

### **1. Clone the Repository**
```bash
git clone https://github.com/your-username/NeuralOperators-WindPrediction.git
cd NeuralOperators-WindPrediction
```

### **2. Install Dependencies**
Install the required Python packages:
```bash
pip install -r requirements.txt
```

### **3. Download Datasets**
Since the raw datasets are large, download them from the ERA5 portal and place them in the project directory. Use the following constraints:
- **Variables**: `u10`, `v10`
- **Region**: Indian subcontinent
- **Time**: Specify training and testing periods

### **4. Run the Notebook**
Execute the Jupyter Notebook to preprocess the data, train the model, and make predictions:
```bash
jupyter notebook neuralOperators.ipynb
```

---

## **File Structure**
```
/neuralOperators/
│-- neuralOperators.ipynb       # Main Jupyter Notebook
│-- simple_fno2d_model.pth      # Trained model weights
│-- README.md                   # Project documentation
│-- .gitignore                  # Ignored files (e.g., datasets, intermediate files)
```

---

## **Future Work**
1. **Incorporate Additional Variables**:
   - Include temperature, pressure, and humidity for multi-variable modeling.
2. **Test on Other Regions**:
   - Generalize the model to other geographical areas.
3. **Improve Model Performance**:
   - Experiment with hyperparameters and deeper architectures.
4. **Deploy as an API**:
   - Serve predictions through a web interface for real-time applications.

---

## **License**
This project is licensed under the MIT License.

---

## **Acknowledgments**
- ERA5 Dataset by ECMWF
- Fourier Neural Operator research from the original paper: "Fourier Neural Operator for Parametric PDEs"

---

## **Contact**
For questions or collaboration opportunities, please contact:
- **Your Name**: jatinvarma708@gmail.com

