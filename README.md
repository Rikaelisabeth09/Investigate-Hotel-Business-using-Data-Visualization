# Investigate-Hotel-Business-using-Data-Visualization
**Table of Contents**
- [Problem Statement](#problem-statement)
    - [Data overview](#data)
    - [Project Review](#projectreview)
    - [Objective](#objective)
- [Data Preprocessing](#data-prepocessing)
    - [Handling Data](#stage-1-data-prepocessing)
- [Data Analysis](#data-analysis)
    - [Monthly Hotel Booking Analysis Based on Hotel Type](#1-monthly-hotel-booking-analysis-based-on-hotel-type)
    - [Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates](#2-impact-analysis-of-stay-duration-on-hotel-bookings-cancellation-rates)
    - [Impact Analysis of Lead Time on Hotel Bookings Cancellation Rates](#3-impact-analysis-of-lead-time-on-hotel-bookings-cancellation-rates)
- [Business Recommendation](#business-recomendation)

## Problem Statement 
## Data
The data used in this project consists of 29 columns and 119390 rows. Data can be accessed, This project's creation makes the assumption that the data is either from an order placed in 119390 or that there are no duplicates.  The following is a description of each column in the data set.
| Column        | Description |
|:-------------|:-----|   
|hotel|  The datasets contains the booking information of two hotel. One of the hotels is a resort hotel and the other is a city hotel|
|is_canceled|  Value indicating if the booking was canceled (1) or not (0)
|lead_time|  Number of days that elapsed between the entering date of the booking into the PMS and the arrival date
|arrival_date_year|  Year of arrival date
|arrival_date_month|  Month of arrival date with 12 categories:'January' to 'December'
|arrival_date_week_number|  Week number of the arrival date
|arrival_date_day_of_month|  Day of the month of the arrival date
|stays_in_weekend_nights|  Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel
|stays_in_weekdays_nights|  Number of week nights (Monday to Friday) the guest stayed or booked to stay at the hotel BO and BL/Calculated by counting the number of week nights
|adults|  Number of adults
|children|  Number of children
|babies|  Number of babies
|meal|  Meal menu
|city|  City of origin
|market_segment|  Market segment designation. In categories, the term “TA” means “Travel Agents” and “TO” means “Tour Operators”
|distribution_channel|  Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators”
|is_repeated_guest|  Value indicating if the booking name was from a repeated guest (1) or not (0)
|previous_cancellations|  Number of previous bookings that were cancelled by the customer prior to the current booking
|previous_bookings_not_canceled|  Number of previous bookings not cancelled by the customer prior to the current booking
|booking_changes|  Number of changes/amendments made to the booking from the moment the booking was entered on the PMS until the moment of check-in or cancellation
|deposit_type|  No Deposit – no deposit was made; Non Refund – a deposit was made in the value of the total stay cost; Refundable – a deposit was made with a value under the total cost of stay
|agent|ID of the travel agency that made the booking
|company|ID of the company/entity that made the booking or responsible for paying the booking. ID is presented instead of designation for anonymity reasons
|days_in_waiting_list| Number of days the booking was in the waiting list before it was confirmed to the customer
|customer_type| Customer Type refers to the categorization of customers based on their relationship with the hotel and the nature of their booking. This categorization helps in understanding customer behavior, preferences, and patterns, and can be used to tailor marketing strategies, improve customer service, and optimize operational efficiency.
|adr| Average Daily Rate (Calculated by dividing the sum of all lodging transactions by the total number of staying nights)
|required_car_parking_spaces| Number of car parking spaces required by the customer
|total_of_special_requests| Number of special requests made by the customer (e.g. twin bed or high floor)
|reservation_status| Check-Oucustomer has checked in but already departed
<br>

## Project Overview
“It is crucial for a company to constantly analyze its business performance. This time, we will
delve deeper into the hospitality industry. Our focus is to understand customer behavior in
booking hotels and its relation to the hotel booking cancellation rate. The insights we find will be
presented in the form of data visualizations to make them easier to understand and more
persuasive.”

## Objective
1. Monthly Hotel Booking Analysis Based on Hotel Type
2. Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates
3. Impact Analysis of Lead Time on Hotel Bookings Cancellation Rate


## Data Prepocessing
- Handling missing values
    1. 'agent`' and '`children`' Columns: Missing values are replaced with 0. This suggests that in these cases, no
`agent` or `children` information was originally provided in the dataset.
    2. `city`' Column: Missing values are filled with 'Unknown'. This approach ensures that records without `city` information can still be included in the analysis, albeit labeled as 'Unknown'.
    3. The '`company`' column is removed because more than 90% of the '`company`' column's values were missing. This high rate of missing data makes the column impractical for meaningful analysis or predictions. By removing it, the dataset is simplified, focusing on columns that contain more complete and informative data.
- Replace Values
     1. Utilize cancel_mapping andrepeat_mapping dictionaries to map numerical values (0 and 1) to descriptive categories ('not canceled'/'canceled' and 'first time'/'repeat') in 'is_canceled' and 'is_repeated_guest' columns.
     2. Replacement of undefined values in 'meal', 'market_segment' , and 'distribution_channel' columns with 'Others'
The 'meal' column is replaced with 'Others' for 'Undefined' values. The 'market_segment' column is replaced with 'Others' for 'Undefined' values. The 'distribution_channel' column is replaced with 'Others' for 'Undefined' values.

- Drop Values
    1. There are 180 data records where all guest categories (children, adults, and babies) are zero. A new DataFrame df_copy_clean is created excluding these records, ensuring valid booking data with at least one guest specified 

**For the detail kindly to check notebook**

## Data Analysis
### 1. Monthly Hotel Booking Analysis Based on Hotel Type
![Monthly Hotel Booking Analysis Based on Hotel Type](https://github.com/Rikaelisabeth09/Investigate-Hotel-Business-using-Data-Visualization/blob/main/Monthly%20Hotel%20Booking%20Analysis%20Based%20On%20Hotel%20Type.png)
Insight:

Overall Trends:
- City Hotels experience a significant increase in bookings from March to August, peaking in August. This indicates that urban areas might be more attractive for travelers during the summer, potentially due to various events, conferences, and tourism activities.
- Resort Hotels see a peak in bookings during the summer months (June to August) but maintain a more steady booking pattern compared to City Hotels. This suggests that resorts are consistently appealing during the summer vacation period.

Monthly Bookings:
- City Hotels have higher booking counts than Resort Hotels throughout the year, indicating a consistently higher demand for city accommodations. This could be due to business travel, urban tourism, and other factors driving people to cities.
- Resort Hotels have a more consistent month-to-month booking pattern compared to City Hotels, suggesting a stable but lower demand. This consistency could be due to the nature of resort stays, which are often planned vacations.


### 2. Impact Analysis of Stay Duration on Hotel Bookings 
![Impact Analysis of Stay Duration on Hotel Bookings](https://github.com/Rikaelisabeth09/Investigate-Hotel-Business-using-Data-Visualization/blob/main/Impact%20Analysis%20of%20Stay%20Duration%20.png)

Insight:
The distinct patterns of hotel booking cancellations between city hotels and resort hotels are quite intriguing. The data reveals that:
1.   The city hotel cancellation rate is generally higher and more volatile compared to the resort hotel, especially for stay durations under 10 nights.
2.   However, the city hotel cancellation rate starts to increase significantly once the stay duration exceeds 10 nights.
3.   In contrast, the resort hotel cancellation rate remains relatively stable until the 16+ night stays, where it then increases more sharply.

These divergent patterns suggest that guests staying at city hotels tend to be more flexible in adjusting their travel plans, particularly for longer durations. On the other hand, resort hotel guests appear to be more committed to their bookings, especially for shorter stay periods.


### 3. Impact Analysis of Lead Time on Hotel Bookings 
![Impact Analysis of Lead Time on Hotel Bookings](https://github.com/Rikaelisabeth09/Investigate-Hotel-Business-using-Data-Visualization/blob/main//Impact%20Analysis%20Of%20Lead%20Time%20On%20Hotel%20Bookings%20Cancellation%20Rates.png)

Insight:
-   `City Hotels`: Higher cancellation rates, increasing with longer lead times, peaking at 0.79 for bookings over 12 months in advance.
-   `Resort Hotels`: Lower and more stable cancellation rates, with a maximum of 0.47 for bookings over 12 months in advance.

## Business Recommendation
### 1. Monthly Hotel Booking Analysis Based on Hotel Type
- Marketing and Promotions: City Hotels should focus marketing efforts on the
summer months to maximize on the peak period, while also creating strategies
to boost bookings during the off-season (e.g., special offers or events). Resort
Hotels can benefit from targeting the summer vacation crowd but should also
look into stabilizing demand during the non-peak periods.
- Resource Allocation: Understanding these trends allows both City and Resort
Hotels to allocate resources, such as staffing and inventory, more effectively to
handle peak seasons and optimize operations during low seasons.
- Event Planning and Partnerships: City Hotels can leverage events and
conferences to drive bookings, especially during peak months. Resort Hotels
might benefit from partnerships with travel agencies and vacation planners to
attract steady bookings throughout the year

### 2. Impact Analysis of Stay Duration on Hotel Bookings 
- Targeted Marketing Strategies:
Hotels can use this information to
develop targeted marketing strategies.
For city hotels, it may be beneficial to
offer incentives for longer stays to
reduce the high cancellation rates. For
resort hotels, maintaining high
customer commitment levels through
personalized experiences and loyalty
programs could be key.
- Dynamic Pricing Models:
Implementing dynamic pricing models
that consider stay duration and
cancellation patterns can help optimize
revenue. City hotels might consider
stricter cancellation policies for longer
stays, while resort hotels could
maintain flexible policies for short
stays.
- Operational Adjustments:
Understanding these patterns can help
in better forecasting and resource
allocation. City hotels may need to
maintain more flexible operations to
accommodate frequent booking
changes, while resort hotels can focus
on providing a consistent guest
experience for shorter, more stable
stays.

### 3. Impact Analysis of Lead Time on Hotel Bookings

City Hotels:
- Flexible Cancellation Policies: Introduce more
flexible cancellation policies to accommodate the
higher variability in cancellations. For example,
offering free cancellation up to a certain number
of days before the stay.
-Incentives for Early Bookings: Provide incentives
for early bookings, such as discounts or
complimentary services, to encourage guests to
commit to their bookings.
- Targeted Marketing: Focus marketing efforts on
shorter lead time bookings to minimize
cancellations. Highlight the convenience and
advantages of last-minute stays.

Resort Hotels:
- Maintaining Stability: Continue to offer stable and
attractive packages for short-term bookings,
ensuring guests remain committed.
- Long-term Booking Packages: Create special
packages for long-term bookings to maintain low
cancellation rates. These could include flexible
rescheduling options or bundled experiences.
- Loyalty Programs: Strengthen loyalty programs to
enhance customer commitment and reduce
cancellation rates. Offer rewards for repeat
bookings and long-term stays.
