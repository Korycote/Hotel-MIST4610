MIST4610 Group 4 Project 1
Team Name
21479 Group 4

Team Members
Raines Harvard @RainesHarvard237
Grace Klatt @gracecklatt
Rocco Garcia @roccog2024
Kory Cote @Korycote
Problem Description
The goal of this project is to model and build a relational database for the general operations of an organization. For our project we decided to create our data model for a fully functioning service hotel. The central entity in the model is Reservation which allows a tie to guest, rooms, employees, promotions, and financial data. The hotel operates a variety of departments and services, including a bar and restaurant, housekeeping, maintenance, and promotional campaigns. Our goal is to accurately model these relationships and generate sample data similar to that of a real hotel. Additionally, we will use the data model to create queries that can provide business insight into a hotel's daily operations, revenue performance, and service efficiency.

Data Model
Explanation of data model: Our model is based on the structure of a full-service hotel.

The Reservation entity is the central hub of the data model. Each reservation is linked to one guest and tracks when they will check in/out, and the status of their booking. A reservation can include multiple hotel rooms and a room can appear in multiple reservations over time. The Reservation_Room entity is an associative entity which resolves the many to many relationship that occurs between Reservation and Room. This allows the actual move in/out datetimes for each room assigned; allowing the hotel to keep track of which rooms are available and which are not.

The Room entity represents each individual room in the hotel, including the floor and status of the room. Each room belongs to a Room_Type which gives the room a categorization (ex: Standard, Double, King, Presidential Suite) and defines the occupancy limits, bed configuration, and nightly rate. Room_Type and Room have a one-to-many relationship allowing the hotel to manage pricing at each category level.

The Guest entity stores the personal information of each individual who makes a reservation at the hotel, including their name, contact information. A guest is able to have many reservations at a time, establishing a one-to-many relationship between Guest and Reservation.

The Promotion entity stores information about the promotion name, scope, percentage, and applicable date range. Promotions are tied to specific room types and are also linked to reservations so that the discount can be properly tracked throughout the booking process.

The Invoice entity captures the billing summary for each reservation, including the total amount, invoice date, and the payment status. Payments separate from the invoice, are tracked separately in the Payment entity, which records the amount paid, method, and datetime allowing the partial payments to be modeled over time.

The Employee entity stores all the information about the hotel staff. It includes their name, role, and hire date. The employee table includes a recursive relationship to model a supervisor hierarchy. Employees are assigned to specific departments through the associative entity, Department_Assignment. This entity tracks the start and end dates of each assignment so the department history can be preserved.

The Department entity represents operational divisions of the hotel (ex: front desk, housekeeping, food and beverages). Each department can have many employees and can be linked to restaurant and bar entities.

The Restaurant entity represents the hotel's dining establishments, each with a cuisine type, seating capacity, and meal service designation (room service or in house dining). Restaurants share Menu_Items with the bar and menu pricing and a category. The Bar entity represents the hotel's bar venue which is separate from the restaurants. The Bar entity has its own seating capacity, bar type, and operating hours.

The Service_Order entity is an associative entity to connect a reservation to the bar or restaurant. Each Service_Order is timestamped and contains many individual items captured in Order_Line_Item, which records the menu item, quantity, and line total.

The HouseKeeping_Record entity tracks each instance of a room being cleaned during or after reservations. Each record links a room, an employee, and a reservation. It also captures the cleaning type, date, status of the room, and any notes made by the housekeeper. Additionally, we created a Maintenance_Request entity to record any issues reported for a specific room and the employees' resolution. It tracks the issues description, priority, status, and both the reported and resolved dates.

Lastly, the Review entity allows quests to leave a review, star rating, any comments they want to share regarding reservation. Each review is tied to one reservation, which allows guests to share any feedback.

correct data model for project 1
Data Dictionary
Table: Reservation Reservaion

Table: Reservation_Room Res_room

Table: Room Room

Table: Room_Type Room_type

Table: Guest Screenshot 2026-03-30 at 7 50 35 PM

Table: Promotion Promotion

Table: Invoice Invoice

Table: Payments Payment

Table: Employee Employee

Table: Department_Assignment Dep_ass

Table: Department Dep

Table: Resturant Resturaunt

Table: Menu_Item Menu_item

Table: Bar image

Table: Service_Order Service_order

Table: Order_Line_Item Order_line_item

Table: HouseKeeping_Record Housekeeping_record

Table: Maintenance_Request Maintence_req

Table: Review Review

Queries:
image
Lists the total food and beverage revenue generated by each department, calculated by summing all order line items totals for service orders linked to each departments resturants.
image
Query 1 allows the hotel management to evaluate which departments are generating the most revenues involving food and beverage sales. This helps employees and the executive staff decide where to invest in staffing and or marketing, and can also help identify which departments are underperforming. This will allow them to identify which may need review or restructuring.

Lists the names and emails of guests whose total spending across all reservations exceeds the average invoice amount, place the ordered by total spend in descending order.
image
Query 2 allows management to identify high-value guests who spend above the average guest. This allows them to identify who may qualify for VIP programs, complimentary upgrades and loyalty incentives. This information can also be used to maximize guest retention rate.

Lists all rooms that have no associated records in the the Maintenance_Request table, including which room they are in, the type of room and the floor.
image
Query 3 helps employees identify which rooms have no maintenance history and if they are overdue for an inspection or have unreported maintenance. It gives management a clear picture of the best kept rooms so they can place premium guest in them or those staying for extended periods.

Calculate the average guest review rating for each room type, along with the total number of reviews submitted, ordered by average rating descending.
image
Query 4 allows hotel management to better understand how guest satisfaction correlates with the category of room they stayed in. If suite guests are rating there stays lower than standard room guests, it can help management identify a service or amenity gap.

Give the names of all employees who cleaned a room where the notes mention - something dirty or damaged.
image
Query 5 finds the names of employees who cleaned a room where something was noted as dirty or damaged, this helps management note where items may need to be replaced or checked up on.

Lists the five items that have generated the highest the highest total revenue across all service orders, including the outlet they belong to and total units sold.
image
Query 6 identifies the hotel's best-selling menu items by total revenue. The managers of the resturants and bars can use this information to feature top performers in promotions, ensure ingredient inventory is fully stocked and evaluate if any adjustments need to be made to inhance profit margin.

Lists the invoice with the most expensive reservation.
image
Query 7 allows hotel management to identify which guest associated with the highest invoice total in the system. It helps staff and executives see which reservation generated the most revenue, which can be useful for tracking high-value guests and allow the company to capitalize off them. This query also allows them to review financial billing activities.

Lists how many times the most popular menu item was consumed.
image
Query 8 helps depict how often the most popular menu item was ordered. This aids the restaurant when designing new menus and cuisine. They can design their menus around what customers are ordering.

Calculate the percentage of guests that paid for their reservation with a credit card.
image
Query 9 counts the number of employees who have held the role of "front desk agent." It works by filtering the Employee table for only those records where the role column matches the title "front desk agent" and uses the COUNT(*) function to return the total number. This helps mangement organize how many staff members are assigned to the front desk.

Lists the payment ID made in July 2025
image
Query 10 selects the payment_id column and filters to show where the payment_date column year is 2025 and the month is July. This is helpful to track payments recieved in a specific month and year.
