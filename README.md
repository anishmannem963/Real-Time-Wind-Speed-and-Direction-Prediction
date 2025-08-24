# Wind Speed and Wind Direction Prediction using Deep Learning

## 🌪️ Project Overview

This project was developed during an internship at **ISRO (Indian Space Research Organisation)** and focuses on predicting wind speed and wind direction using deep learning techniques and time series analysis. The system analyzes 6 hours of historical meteorological data to accurately forecast wind conditions for 1 hour into the future.

## 🎯 Objectives

- Develop a robust wind speed and direction prediction model using deep learning
- Process and analyze historical wind data with time series analysis
- Handle missing data efficiently using advanced data preprocessing techniques
- Provide accurate 1-hour wind forecasting for various applications
- Support renewable energy, transportation, and emergency management sectors

## 🚀 Technologies Used

### Programming Language
- **Python**: Core development language chosen for its extensive library ecosystem and user-friendly syntax

### Libraries & Frameworks
- **TensorFlow**: Deep learning framework for building and training neural networks
- **NumPy**: High-performance multidimensional array operations
- **Pandas**: Data manipulation and analysis
- **Matplotlib**: Data visualization and plotting
- **MySQL Connector**: Database connectivity and operations

### Database
- **MySQL**: Storage and management of meteorological data

### Analysis Techniques
- **Time Series Analysis**: Statistical modeling of time-based wind data
- **Deep Learning**: Neural network-based prediction models
- **Feature Engineering**: Extraction of temporal and seasonal patterns

## 🏗️ System Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────────┐
│   Raw Wind Data │ ── │  Data Processing │ ── │  Feature Engineering│
│   (1-sec data)  │    │  (5-min intervals)│    │  (u, v components)  │
└─────────────────┘    └──────────────────┘    └─────────────────────┘
                                │
                                ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────────┐
│   Visualization │ ◄─ │  Model Training  │ ◄─ │    Data Storage     │
│   & Comparison  │    │  & Prediction    │    │   (MySQL Database)  │
└─────────────────┘    └──────────────────┘    └─────────────────────┘
```

## 📊 Workflow

1. **Data Loading**: Import historical wind speed data from database
2. **Data Preprocessing**: 
   - Convert 1-second data to 5-minute intervals
   - Handle missing values using pandas grouper function
   - Normalize data for neural network input
3. **Feature Engineering**:
   - Extract temporal features (hour, day, week, month, season)
   - Calculate wind components (u, v vectors)
   - Create cyclical time features
4. **Model Training**: Train deep learning models for wind prediction
5. **Evaluation & Forecasting**: Generate 1-hour predictions
6. **Visualization**: Compare actual vs predicted values

## 💾 Database Schema

The project uses several MySQL tables:
- `WindSpeed_4_2023`: Raw wind speed data
- `winddir_4_2023`: Raw wind direction data
- `convert_2_5_min_data`: Processed 5-minute interval data
- `prediction_u1`: U-component predictions
- `prediction_v1`: V-component predictions

## 🔧 Installation & Setup

### Prerequisites
```bash
Python 3.7+
MySQL Server
```

### Required Libraries
```bash
pip install tensorflow
pip install pandas
pip install numpy
pip install matplotlib
pip install mysql-connector-python
```

### Database Configuration
```python
config = {
    'host': '127.0.0.1',
    'port': 3306,
    'database': 'wind',
    'user': 'your_username',
    'password': 'your_password',
    'charset': 'utf8'
}
```

## 🎮 Usage

### 1. Data Conversion
Convert raw 1-second data to 5-minute intervals:
```bash
python ConversionFrom1SecTo5Mins.py
```

### 2. Wind Speed Prediction (U-component)
```bash
python prediction_u.py
```

### 3. Wind Direction Prediction (V-component)
```bash
python prediction_v.py
```

### 4. Generate Comparison Graphs
```bash
python graph_wind_speed.py
python graph_wind_direction.py
```

## 📈 Results & Performance

### Key Achievements
- **Forecast Horizon**: 1-hour accurate predictions
- **Data Processing**: Efficient handling of missing data using 5-minute interval grouping
- **Model Performance**: Successful prediction of both wind speed and direction
- **Temporal Features**: Integration of seasonal, hourly, and daily patterns

### Visualization Outputs
- Wind Speed Prediction graphs comparing actual vs predicted values
- Wind Direction Prediction charts showing model accuracy
- Time series plots demonstrating temporal patterns

## 🔬 Technical Highlights

### Data Preprocessing Innovation
- **Interval Conversion**: Transform high-frequency (1-second) data into manageable 5-minute intervals
- **Missing Data Handling**: Utilize pandas grouper function for robust data imputation
- **Feature Normalization**: Apply statistical normalization for neural network optimization

### Deep Learning Architecture
- **Input Features**: Year, season, month, week, day-of-year, hour, minute, wind components
- **Model Type**: Time series forecasting neural network
- **Output**: 12-step ahead predictions (1 hour with 5-minute intervals)

### Wind Component Analysis
```python
# U-component (East-West)
df['u'] = -(df['ws100'] + 0.000000001) * np.sin(np.deg2rad(df['wd100']))

# V-component (North-South)  
df['v'] = -(df['ws100'] + 0.000000001) * np.cos(np.deg2rad(df['wd100']))
```

## 🌟 Applications

### Renewable Energy
- Wind farm optimization
- Power generation forecasting
- Turbine maintenance scheduling

### Transportation
- Aviation weather services
- Maritime navigation
- Ground transportation safety

### Emergency Management
- Severe weather prediction
- Disaster response planning
- Public safety alerts

## 📊 Project Impact

This research demonstrates significant contributions to meteorological forecasting:

- **Accuracy**: Successfully predicts wind conditions using 6 hours of historical data
- **Efficiency**: Automated data processing pipeline handles large-scale meteorological datasets
- **Reliability**: Robust handling of missing data ensures consistent predictions
- **Scalability**: Framework can be extended to other meteorological parameters

## 🔮 Future Enhancements

- Integration of additional meteorological parameters (temperature, pressure, humidity)
- Extended forecast horizons (6-12 hour predictions)
- Real-time streaming data processing
- Web-based dashboard for visualization
- Integration with weather station networks
- Mobile application development

## 🤝 Contributing

This project was developed as part of an ISRO internship program. For academic or research collaborations, please refer to ISRO's collaboration guidelines.

## 📄 License

This project was developed under ISRO's internship program. Please respect intellectual property and usage guidelines.

## 🏢 Organization

**Indian Space Research Organisation (ISRO)**
- Department of Space, Government of India
- Atmospheric and meteorological research division

## 👨‍💻 Development Team

Developed during ISRO internship program focusing on meteorological data analysis and prediction systems.

---

*This project represents a significant step forward in automated wind prediction systems, combining advanced deep learning techniques with practical meteorological applications.*
