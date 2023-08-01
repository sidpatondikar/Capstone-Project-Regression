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



To enhance the performance of the model, additional features have been generated. These new features aim to provide more relevant information and contribute to improved predictions. The dataset has been subjected to testing using multiple regression models. These models have been employed to analyze the data and derive insights, allowing for a comprehensive evaluation of the predictive capabilities. The most significant features identified by the model are highlighted and displayed. These key features play a crucial role in determining the number of seats sold for each ride. By showcasing these important factors, stakeholders can gain a better understanding of the influential elements driving seat sales.
