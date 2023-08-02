![image](https://github.com/sidpatondikar/Capstone-Project-Regression/assets/83869822/8af25c02-ac73-40ef-b235-7d8cf5063b26)


# Capstone - Transport Demand Prediction

-----------------------------------

## Project Summary

In summary, the project aims to create a model that predicts the number of seats sold for each ride on specific routes, dates, and times for Mobiticket. The routes originate from 14 towns towards Lake Victoria, ending in Nairobi. The journey takes around 8 to 9 hours to reach the outskirts of Nairobi and an additional 2 to 3 hours to reach the main bus terminal. Passengers are influenced by traffic conditions during their travel into the city and onward to their final destinations in Nairobi. Understanding these patterns can help improve service planning and optimize operations for Mobiticket.

-------------------------------------
### Variables in data:

- ride_id: unique ID of a vehicle on a specific route on a specific day and time.
- seat_number: seat assigned to ticket
- payment_method: method used by customer to purchase ticket from Mobiticket (cash or Mpesa)
- payment_receipt: unique id number for ticket purchased from Mobiticket
- travel_date: date of ride departure. (MM/DD/YYYY)
- travel_time: scheduled departure time of ride. Rides generally depart on time. (hh:mm)
- travel_from: town from which ride originated
- travel_to: destination of ride. All rides are to Nairobi.
- car_type: vehicle type (shuttle or bus)
- max_capacity: number of seats on the vehicle
-----------------------------------------

### Data Wrangling

- Created target variable 'number_of_ticket'
- Dropped constant and non essential columns
- Used travel_date and travel_time columns to extract and create datetime related features
- Created period feature from travel time for data visualization

-------------------------------------------

### Exploratory Data Analysis

#### Key Insights:
![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/c39879c1-2e95-402c-b1e1-d55e4723dd07)
- For each ride, most of the tickets sold is less than 11. 

![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/57ac6cac-6dfc-4b4e-bd61-ca4ac119fd75)
- Most of the tickets are sold in month of December, followed by Feb and Jan

![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/c62518c7-74a3-459d-b3cd-6cd0635e7339)

- There are no tickets sold between 5th and 11th of every month. Transport may be closed during this period every month because of tranport holiday.

![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/70c96114-b3b0-46a7-8daa-e6f47aed0713)

- In the day, most tickets are sold at 7AM and close to 7PM. This can be because people going to work in Nairobi at these times. Similarly, there are no tickets sold between 12PM and 5:30 PM.

#### Other insights
- The number of Buses and shuttle are nearly equal in the data. Hence, both type of cars are used equally for traveling.
- Buses have max capacity of bus is 49, whereas max capacity of shuttle is 11.
- Most number of tickets are sold from:  Sirare,  Mbita,   Migori
- While the least number of tickets are sold from: Keumbu, Kendu Bay

-------------------------------------------------------------
### Feature Engineering and Data Preprocessing

To enhance the performance of the model, additional features have been generated. These new features aim to provide more relevant information and contribute to improved predictions. These include:

- Some columns travel_month, travel_day_of_year, travel_day_of_month and time_period_of_day have skewed data, to handle this, new weight wise columns have been created by taking log transformation.
- How frequently the bus arrives at every source destination can be a major factor effecting the number of tickets sold on that route. Hence, the following columns are created based on the frequency of bus/shuttle arriving :
    - Time_gap_btw_0_1_next_bus
    - Time_gap_btw_0_1_previous_bus
    - Time_gap_btw_0_2_next_bus
    - Time_gap_btw_0_2_previous_bus
    - Time_gap_btw_0_3_next_bus
    - Time_gap_btw_0_3_previous_bus
    - Time_gap_btw_next_previous_bus
- The distance of source to destination (Nairobi) can also be a major factor effecting the number of tickets, hence, a new column called distance_to_destination is created containing distances of all the 14 sources to Nairobi.
- To deal with multicollinearity, few of the columns are dropped.
- Categorical encoding is done on few columns and finally data is split into training and test.
------------------------------------------------------------------

### ML Model Implementation
- Five models are implemented to predict the transport demand to Nairobi. These include:
    - Linear Models:
        - Linear Regression
        - Lasso Regression (L1)
        - Ridge Regression (L2)
    - Ensemble Models:
        - Random Forest
        - XGBoost
- To improve model performance, k-fold cross validation and hyperparamter tuning is done using GridSearchCV.
- Evaluation metrics such as MSE, RMSE, MAE, MAPE, R2 score and Adjusted R2 score is used to compare model performance
- Final model comparision on test data accuracy:
  
![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/e544d398-d339-43f5-8e35-628f0c4fe5f5)

- Hyperparamter tuned Random Forest model gave the best test accuracy, hence it it chosen as final prediction model.

### Feature Importance
![image](https://github.com/sidpatondikar/Capstone-Transport-Demand-Prediction/assets/83869822/6ab48e16-1f24-464d-bef1-e48f3ae50486)

The most significant features identified by the model are highlighted and displayed. These key features play a crucial role in determining the number of tickets sold for each ride. By showcasing these important factors, stakeholders can gain a better understanding of the influential elements driving ticket sales.

-------------------------------------------------------------------------
### Conclustion

- In this project, we have used different regression models to predict transport demand from various places to nairobi.

- Using the data, we have created the target variable and several other features that contribute to our model performance.

- We have used regression models including:

    Linear Models : Linear Regression, Lasso (L1), Ridge (L2)
    Non Linear Models: Random Forest, XGBoost.
    We have also performed hyperparameter tuning to improve the performance of these models.

- Out of all these models, the hyperparameter tuned Random Forest gives the best result with an accuracy of around 94%.

- Most important features came out to be distance_to_destination followed by Time_gap_btw_0_1_next_bus and travel_day_year_wise_weights.
