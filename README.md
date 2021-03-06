# Hotel_Reservation_Prediction
 EDA & Classification on Kaggle Hotel Booking dataset

## Description

In this notebook, I did an exploratory data analysis and a classification using **Random Forest model** on Kaggle's [Hotel Booking dataset](https://www.kaggle.com/jessemostipak/hotel-booking-demand). Specifically, I 

 - analyzed the **general shape and columns** of the dataset
 - examined the **4 columns that contain missing values and if to impute or drop them** in the dataset
 - made **univariate data analysis with 9 customer-related columns** to acquire a general idea about the hotel customers, and 
 - evaluated **6 classification algorithms** and **predicted users' reservation cancellation** chance using Random Forest model. 
 
 After tuning the parameters and modifying the required_car_parking_spaces column, the model achieves a cross-validation accuracy of **87.12%**.
 
## EDA Samples

Here are some of the properties of the data I looked at for my EDA. 
<p align="left">
  <img width="800" height="90" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/data_shape.jpg">
</p>

<p align="left">
  <img width="800" height="200" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/data_missing.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/hotel_distribution.jpg">
</p>
 
<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/guest_home.jpg">
</p>

## Prediction

To effectivelly predict if a customer will cancel the booking, I looked at the columns that have the highest correlations with the cancellation column as well as the relationships between categorical features with the cancellation column. 

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/cancel_corr.jpg">
</p>

When selecting features, to prevent possible data leakage, I excluded booking_changes, which may include the final cancellation of hotel reservation. Furthermore, reservation_status also may include whether a customer cancels the booking or not. So I also omitted that one. Thus, from the analysis, I selected these variables as input.

<p align="left">
  <img width="800" height="300" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/selected_features.jpg">
</p>

Then I implmented six classification algorithms using these features as input and checked the models' cross-validation accuracy with the dataset. From the results I decided to use Random Forest classifier for this task as it has the highest baseline accuracy.

<p align="left">
  <img width="800" height="100" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/baseline_accuracy_after_binary.jpg">
</p>

For each column with high correlation, I visualized the association between the column and the cancellation column. Specifically, I found that if the customer requires at least one parking space, the chance to cancel the reservation is minimal:

<p align="left">
  <img width="800" height="200" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/car_parking_cancel.jpg">
</p>

Therefore, I decide to transform this column into a two-classes column that only has 0(which means the customer doesn't require parking space) and 1(which means the customer requires parking space). The modification is as follows:

Before Modification:

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/car_parking_dist.jpg">
</p>

After Modification:

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/car_parking_binary.jpg">
</p>

<p align="left">
  <img width="800" height="150" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/car_parking_binary_cancel.jpg">
</p>

With this modification, the max and min score of the model both increased slightly:

<p align="left">
  <img width="800" height="100" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/improved_accuracy.jpg">
</p>

Finally, after tuning the parameters, the performance of the model is about **87.12%**.

<p align="left">
  <img width="800" height="100" src="https://github.com/RandomY-2/Hotel_Reservation_Prediction/blob/main/images/final_accuracy.jpg">
</p>
