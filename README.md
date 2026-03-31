# MIST4610 Group 4 Project 1 
# Team Name 
21479 Group 4
## Team Members 
 1. Raines Harvard [@RainesHarvard237](https://github.com/RainesHarvard237/Raines-Harvard-Group-4-MIST-Project-1-Hotel)
 2. Grace Klatt [@gracecklatt](https://github.com/gracecklatt/MIST-4610-Hotel/blob/main/README.md)
 3. Rocco Garcia [@roccog2024](https://github.com/roccog2004/Group4Project)
 4. Kory Cote [@Korycote](https://github.com/Korycote/Hotel-MIST4610)

## Problem Description
The goal of this project is to model and build a relational database for the general operations of an organization. For our project we decided to create our data model for a fully functioning service hotel. The central entity in the model is Reservation which allows a tie to guest, rooms, employees, promotions, and financial data. The hotel operates a variety of departments and services, including a bar and restaurant, housekeeping, maintenance, and promotional campaigns. Our goal is to accurately model these relationships and generate sample data similar to that of a real hotel. Additionally, we will use the data model to create queries that can provide business insight into a hotel's daily operations, revenue performance, and service efficiency.
# Data Model
Explanation of data model:
Our model is based on the structure of a full-service hotel.

The **Reservation** entity is the central hub of the data model. Each reservation is linked to one guest and tracks when they will check in/out, and the status of their booking. A reservation can include multiple hotel rooms and a room can appear in multiple reservations over time. The **Reservation_Room** entity is an associative entity which resolves the many to many relationship that occurs between Reservation and Room. This allows the actual move in/out datetimes for each room assigned; allowing the hotel to keep track of which rooms are available and which are not.

The **Room** entity represents each individual room in the hotel, including the floor and status of the room. Each room belongs to a **Room_Type** which gives the room a categorization (ex: Standard, Double, King, Presidential Suite) and defines the occupancy limits, bed configuration, and nightly rate. **Room_Type** and **Room** have a one-to-many relationship allowing the hotel to manage pricing at each category level.

The **Guest** entity stores the personal information of each individual who makes a reservation at the hotel, including their name, contact information. A guest is able to have many reservations at a time, establishing a one-to-many relationship between Guest and Reservation.

The **Promotion** entity stores information about the promotion name, scope, percentage, and applicable date range. Promotions are tied to specific room types and are also linked to reservations so that the discount can be properly tracked throughout the booking process.

The **Invoice** entity captures the billing summary for each reservation, including the total amount, invoice date, and the payment status. Payments separate from the invoice, are tracked separately in the **Payment** entity, which records the amount paid, method, and datetime allowing the partial payments to be modeled over time.

The **Employee** entity stores all the information about the hotel staff. It includes their name, role, and hire date. The employee table includes a recursive relationship to model a supervisor hierarchy. Employees are assigned to specific departments through the associative entity, **Department_Assignment**. This entity tracks the start and end dates of each assignment so the department history can be preserved.

The **Department** entity represents operational divisions of the hotel (ex: front desk, housekeeping, food and beverages). Each department can have many employees and can be linked to restaurant and bar entities.

The **Restaurant** entity represents the hotel's dining establishments, each with a cuisine type, seating capacity, and meal service designation (room service or in house dining). Restaurants share **Menu_Items** with the bar and menu pricing and a category. The **Bar** entity represents the hotel's bar venue which is separate from the restaurants. The Bar entity has its own seating capacity, bar type, and operating hours.

The **Service_Order** entity is an associative entity to connect a reservation to the bar or restaurant. Each Service_Order is timestamped and contains many individual items captured in **Order_Line_Item**, which records the menu item, quantity, and line total.

The **HouseKeeping_Record** entity tracks each instance of a room being cleaned during or after reservations. Each record links a room, an employee, and a reservation. It also captures the cleaning type, date, status of the room, and any notes made by the housekeeper. Additionally, we created a **Maintenance_Request** entity to record any issues reported for a specific room and the employees' resolution. It tracks the issues description, priority, status, and both the reported and resolved dates.

Lastly, the **Review** entity allows quests to leave a review, star rating, any comments they want to share regarding reservation. Each review is tied to one reservation, which allows guests to share any feedback.

<img width="1269" height="833" alt="correct data model for project 1" src="https://github.com/user-attachments/assets/cc12d5b1-4348-43e1-ae2a-b2b729e9b5e7" />


# Data Dictionary 
**Table: Reservation**
<img width="1092" height="311" alt="Reservaion" src="https://github.com/user-attachments/assets/52461ddb-c26c-41b7-90f8-279160b3bd09" />


**Table: Reservation_Room**
<img width="1086" height="262" alt="Res_room" src="https://github.com/user-attachments/assets/e28f47c8-2de3-478d-93ae-33781b5f9d62" />


**Table: Room**
<img width="1206" height="182" alt="Room" src="https://github.com/user-attachments/assets/9f016377-58bd-43cd-b5c2-265974635a88" />


**Table: Room_Type**
<img width="1063" height="262" alt="Room_type" src="https://github.com/user-attachments/assets/e6ee7b3b-9286-4f30-b97f-0fdfc027bcce" />


**Table: Guest**
<img width="1092" height="256" alt="Screenshot 2026-03-30 at 7 50 35 PM" src="https://github.com/user-attachments/assets/258ff709-0fcf-43a0-a24c-6da4b586077f" />


**Table: Promotion**
<img width="1087" height="298" alt="Promotion" src="https://github.com/user-attachments/assets/6c2c77cc-0ab3-4052-819a-5c52dac80855" />


**Table: Invoice** 
<img width="1090" height="256" alt="Invoice" src="https://github.com/user-attachments/assets/99081fe8-6c73-4882-b1f3-b8d935731ace" />


**Table: Payments**
<img width="1084" height="238" alt="Payment" src="https://github.com/user-attachments/assets/227c2f5e-638b-48a1-81ab-734539d9d6a7" />


**Table: Employee**
<img width="1091" height="273" alt="Employee" src="https://github.com/user-attachments/assets/451b6876-99ff-4470-9daf-d1db8d2b7bb4" />


**Table: Department_Assignment**
<img width="1086" height="269" alt="Dep_ass" src="https://github.com/user-attachments/assets/a5334076-a7fe-4886-b955-e07bc7f7219d" />


**Table: Department**
<img width="1085" height="195" alt="Dep" src="https://github.com/user-attachments/assets/8b895c41-cd49-48c1-9402-fcabce6fa683" />


**Table: Resturant**
<img width="1082" height="266" alt="Resturaunt" src="https://github.com/user-attachments/assets/320d2c77-fbf3-4762-b3e1-75b7211b1e4a" />


**Table: Menu_Item**
<img width="1086" height="273" alt="Menu_item" src="https://github.com/user-attachments/assets/a1b16262-60bc-4c6f-a574-c70e9f9294db" />


**Table: Bar**
<img width="966" height="226" alt="image" src="https://github.com/user-attachments/assets/6e4f428f-99a4-4d56-98ec-fb3d279453d9" />

Table: Service_Order
<img width="1167" height="227" alt="Service_order" src="https://github.com/user-attachments/assets/5ad1db50-4b86-4d67-b77d-de7ce467c4dc" />


**Table: Order_Line_Item**
<img width="1087" height="236" alt="Order_line_item" src="https://github.com/user-attachments/assets/25917ca4-12e0-4858-b021-a941a01196fb" />

**Table: HouseKeeping_Record**
<img width="1087" height="366" alt="Housekeeping_record" src="https://github.com/user-attachments/assets/ca5489be-e85b-4091-aa09-2e249d27f909" />


**Table: Maintenance_Request**
<img width="1089" height="353" alt="Maintence_req" src="https://github.com/user-attachments/assets/956159f7-82b1-431d-af21-06f7198d905a" />


**Table: Review** 
<img width="1088" height="247" alt="Review" src="https://github.com/user-attachments/assets/0b458ca0-a606-47d6-acca-3c491804185b" />


# Queries:
<img width="872" height="312" alt="image" src="https://github.com/user-attachments/assets/122d771a-eca5-49ad-bf48-ed7c5db5ba83" />

1. Lists the total food and beverage revenue generated by each department, calculated by summing all order line items totals for service orders linked to each departments resturants.

<img width="818" height="502" alt="image" src="https://github.com/user-attachments/assets/d05b40a5-f1fe-4fdc-bde1-badb576bee2a" />

Query 1 allows the hotel management to evaluate which departments are generating the most revenues involving food and beverage sales. This helps employees and the executive staff decide where to invest in staffing and or marketing, and can also help identify which departments are underperforming. This will allow them to identify which may need review or restructuring. 

2. Lists the names and emails of guests whose total spending across all reservations exceeds the average invoice amount, place the ordered by total spend in descending order.

<img width="588" height="792" alt="image" src="https://github.com/user-attachments/assets/de118943-c720-442a-891c-36a386e26e3a" />

Query 2 allows management to identify high-value guests who spend above the average guest. This allows them to identify who may qualify for VIP programs, complimentary upgrades and loyalty incentives. This information can also be used to maximize guest retention rate. 

3. Lists all rooms that have no associated records in the the Maintenance_Request table, including which room they are in, the type of room and the floor.

<img width="626" height="823" alt="image" src="https://github.com/user-attachments/assets/caade04b-7beb-49c5-b88a-1454d1417ea1" />

Query 3 helps employees identify which rooms have no maintenance history and if they are overdue for an inspection or have unreported maintenance. It gives management a clear picture of the best kept rooms so they can place premium guest in them or those staying for extended periods. 

4. Calculate the average guest review rating for each room type, along with the total number of reviews submitted, ordered by average rating descending.

<img width="823" height="646" alt="image" src="https://github.com/user-attachments/assets/1e39591c-c43e-436a-8ca2-7b6f1a530802" />

Query 4 allows hotel management to better understand how guest satisfaction correlates with the category of room they stayed in. If suite guests are rating there stays lower than standard room guests, it can help management identify a service or amenity gap. 

5. Give the names of all employees who cleaned a room where the notes mention - something dirty or damaged.
<img width="647" height="797" alt="image" src="https://github.com/user-attachments/assets/0c5b18e2-2796-4f47-b1d3-53a6f098f534" />

Query 5 finds the names of employees who cleaned a room where something was noted as dirty or damaged, this helps management note where items may need to be replaced or checked up on.

6. Lists the five items that have generated the highest the highest total revenue across all service orders, including the outlet they belong to and total units sold.
<img width="817" height="756" alt="image" src="https://github.com/user-attachments/assets/d54dd7fa-7317-4805-88b9-f45fc3832d25" />

Query 6 identifies the hotel's best-selling menu items by total revenue. The managers of the resturants and bars can use this information to feature top performers in promotions, ensure ingredient inventory is fully stocked and evaluate if any adjustments need to be made to inhance profit margin. 

7. Lists the invoice with the most expensive reservation.
<img width="822" height="362" alt="image" src="https://github.com/user-attachments/assets/358f819b-c97f-4d91-aacb-94dabc9399e2" />

Query 7 allows hotel management to identify which guest associated with the highest invoice total in the system. It helps staff and executives see which reservation generated the most revenue, which can be useful for tracking high-value guests and allow the company to capitalize off them. This query also allows them to review financial billing activities.

8. Lists how many times the most popular menu item was consumed.
<img width="823" height="427" alt="image" src="https://github.com/user-attachments/assets/e8f3ba0f-d24d-45f9-86aa-e7bcf1454aa0" />

Query 8 helps depict how often the most popular menu item was ordered. This aids the restaurant when designing new menus and cuisine. They can design their menus around what customers are ordering. 

9. list the number of Employees with the role "Front Desk Agent"
<img width="802" height="421" alt="image" src="https://github.com/user-attachments/assets/4bf6b0f2-0b05-4508-8153-afa1d83c52b6" />

Query 9 counts the number of employees who have held the role of "Front Desk Agent." It works by filtering the Employee table for only those records where the role column matches the title "Front Desk Agent" and uses the COUNT(*) function to return the total number. This helps mangement organize how many staff members are assigned to the front desk. 

10.  Lists the payment ID made in July 2025

<img width="607" height="615" alt="image" src="https://github.com/user-attachments/assets/40fb002b-929b-40d9-8f9c-043618660ece" />

Query 10 selects the payment_id column and filters to show where the payment_date column year is 2025 and the month is July. This is helpful to track payments recieved in a specific month and year. 


