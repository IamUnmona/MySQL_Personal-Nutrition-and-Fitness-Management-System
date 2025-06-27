# MySQL_Personal-Nutrition-and-Fitness-Management-System
This repository contains a comprehensive SQL-based database project that manages and monitors personal nutrition, fitness activities, and health goals. The system is built to cater to individuals aiming for a healthy lifestyle, trainers offering professional guidance, and admins who oversee operations and community engagement.

---

## 📘 Project Overview

The **Personal Nutrition and Fitness Management System** is a robust and scalable SQL project that simulates a real-world application for:

- Storing user and trainer profiles
- Recording workout sessions and fitness progress
- Creating personalized nutrition and exercise plans
- Managing reminders, notifications, and content
- Analyzing user behavior and performance

This project is suitable for academic demonstrations, capstone presentations, or as a backend prototype for a fitness app.

---

## 💾 Database Summary

### 🧍 Users Table (`Users_T1`)
Captures demographic and health-related data such as age, sex, weight, height, dietary restrictions, allergies, and contact information.

### 🏋️ Trainers Table (`Trainers_T2`)
Stores trainer details including specialization, certification, and contact.

### 🗓️ Sessions Table (`Sessions_T3`)
Logs each session (virtual/personal) with date, duration, trainer association, and user rating.

### 📈 Progress Log (`Progress_Log_T4`)
Tracks workout duration, calories burned, and attendance per user.

### 🥗 Nutrition Plans (`NutritionPlan_T5`) and 🍽️ Recipes (`Recipe_T6`)
Designs custom dietary recommendations and references associated recipes.

### 🏃 Exercise Plans (`ExercisePlan_T7`)
Individualized fitness plans including type, duration, frequency, difficulty, and exercises.

### 🎯 Fitness Goals (`FitnessGoals_T8`)
Tracks target achievements and current progress on personalized goals.

### 🔔 Notifications (`Notifications_T9`), 🏠 Addresses (`Addresses_T10`), and ⏰ Workout Reminders (`WorkoutReminder_T11`)
Engage users with location-based updates and personalized alerts.

### 📚 Content (`Content_T12`) and 🧑‍🤝‍🧑 Communities (`Community_T13`)
Stores articles, videos, podcasts, and user communities.

### ⚙️ Sharing Options (`Sharing_Option_T14`), Update Logs (`updated_user_T15`), and Audit Tables
Handles user privacy preferences and logs changes for compliance and traceability.

---

## 🔍 Functional Capabilities

### ✅ Built-In Queries
- Retrieve user profiles with fitness goals and address information
- Find addresses of session-enrolled users for deliveries
- Send notifications based on city
- Analyze workout duration variability and calories burned
- Retrieve top contributors and engagement stats

### 🧠 Functions
- `recommend_calories(weight, height, age, sex)`: Calculates BMR-based daily intake
- `get_bmi(height, weight)`: Computes BMI
- `AverageDuration(userID)`: Returns average workout time

### ⚙️ Stored Procedures
- Insert new users, addresses, and fitness goals
- Update address records

### 🚨 Triggers
- Log user profile updates
- Create audit logs and trigger notifications for goal creation
- Store deleted trainer information

### 🪞 Views
- `User_Goal_Status`: Join of users with fitness goals
- `Trainer_Session_Summary`: Overview of sessions by trainer

### 📈 Indexes
- On names and calorie intake columns to speed up performance

---

## 📁 Repository Structure

```bash
personal-nutrition-fitness-sql-system/
├── database/
│   └── personal_nutrition_fitness.sql        # Full DDL + DML SQL script
├── README.md
├── LICENSE                                   # MIT License (or as preferred)
├── docs/
│   ├── schema_description.md                 # Table descriptions
│   └── ERD_Diagram.png                       # Optional - Entity Relationship Diagram
└── queries/
    └── analytics_queries.sql                 # Selected analytical use cases
```

---

## 🧪 Sample Use Case Queries
```sql
-- Get all users with no fitness goals but have reminders
SELECT Users_T1.User_id_pk, Users_T1.Ufname, Users_T1.Contact
FROM Users_T1
JOIN WorkoutReminder_T11 ON Users_T1.User_id_pk = WorkoutReminder_T11.User_ID_fk
LEFT JOIN FitnessGoals_T8 ON Users_T1.User_id_pk = FitnessGoals_T8.UserID_fk
WHERE FitnessGoals_T8.GoalID_pk IS NULL;

-- Insert a notification for all users in Albany
INSERT INTO Notifications_T9 (User_ID_FK, Notification_Message, Notification_Type)
SELECT User_id_pk, 'Marathon Run in Albany!', 'Event Alert'
FROM Users_T1
JOIN Addresses_T10 ON Users_T1.User_id_pk = Addresses_T10.User_ID_FK
WHERE City = 'Albany';
```

---

## 🚀 How to Run

1. Install MySQL or connect to a cloud-based RDBMS.
2. Clone this repo:
   ```bash
   git clone https://github.com/yourusername/personal-nutrition-fitness-sql-system.git
   ```
3. Execute `database/personal_nutrition_fitness.sql` to create and populate the database.
4. Optionally run `queries/analytics_queries.sql` for analytical insights.


---

## 🧾 License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

## 👤 Author
**Unmona Das**  
 
[LinkedIn](https://www.linkedin.com/in/unmonadas) | [GitHub](https://github.com/IamUnmona)

---

## 🌟 Acknowledgements
This SQL project was developed as part of an academic course on database systems.
