# Housing Price Prediction
This project involves building a housing price prediction model using TensorFlow based on historical housing data from California. 
The goal is to predict housing prices by leveraging various machine learning techniques and neural networks.

## Techniques Used
In this project the following techniques were used: 
- Feature Engineering
- Data Processing
- Data Visualization
- Data Analysis
- Prediction Neural Network

## Tools Used 
- pandas
- numpy
- seaborn
- matplotlib.pyplot
- tensorflow with keras 
- sklearn train_test_split
- python
  
## 1.) Data Extraction 
- Downloaded the data set locally
- and imported the data using pandas

## 2.) EDA (Exploratory Data Analysis)
- Performed operations:
    * info(), describe(), value_counts()
    * isnull().sum()
    * And plotted a histogram for each non categorical feature to view its distribution 
    * Decided to remove rows for all null cells
    * Checked for duplicate rows


![Alt text]( images/Distributions.png )

      
### Conclusions
- Our "median_house_value" and "housing_median_age" appear to be capped at a limit, shown by the large spike/maximum towards the far right of the histogram
  * Two Solutions:
  *   * Either gather more data from districts that were capped
  *   * Or we can remove those pieces of data from the training set
  * It also appears that the "median_income" column is not scaled normally
  * Its also important to note that many histograms represent a tail heavy distribution
      
## 3.) Data Processing 
- We one hot encoded categorical feature ocean_proximity( we had to turn this into integer values due to tensorflows built in one hot encoder not taking categorical values, later I learned just to use pd.get_dummies or sklearn.OneHotEncoder)
- Decided to discard the capped values which was about 4% of the data set 
- Created feaures: 
  * Total rooms per Household
  * Total bedrooms per Household
  * Population per Household

## 4.) Data Visualization 
- Used box plots, histograms, heatmaps, and geographical visualizations to gain insight on the data and understand correlation between features

![Alt text](images/Heatmap.png)

![Alt text](images/GeographicalMap.png)

### Conclusions 

- The only relationship that stands out is the "housing_median_value" vs "median_income". Looking at the scatterplot it may not be immediatly obivous but there is a positive correlation between these two values. To verify this relationship I have also visalued a heat map, which proves that the relationship between these two are positive with a value of 0.69. This intuativley makes sense, as the income in that disctrict increases so do the prices of housing.
  
- This is intersting to look at, intuitively housing prices are more expensive near the coast, from what looks like to be Los Angeles and San Fransico. And we can clearly see how densly packed these locations are. The combination of population density and location in these areas could provide significant data when training our predictive model

## 5.) Model Training 
- I used 3 models each increasing in complexity using Min-Max scaling and Standardization as scaling metrics
- and used MAE as an evalution metric
Here is a run down of each model:

#### Model 1
* 1 Hidden Layer
* 10 epochs
* Standard Gradient Descent as optimzer
* No Change in Learning Rate
* Using MAE

#### Model 2
* 3 Hidden Layers
* Use MAE
* Use 50 Epochs
* Use Activation Function ReLu
* Optimizer Adam
* Learning Rate Adjusted to 0.001
  
#### Model 3
* 5 hidden Layers
* Use MAE
* Use 100 Epochs
* Use Activation Function Leaky ReLu
* Optimizer Adam
* Learning Rate Adjusted to 0.01
