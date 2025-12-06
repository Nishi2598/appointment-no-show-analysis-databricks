# 📊 Medical Appointment No-Show Analysis (Databricks SQL Project)

This project analyzes factors that influence **patient appointment no-shows** using the popular _Medical Appointment No-Show Dataset_.

The goal is to identify key drivers such as age, gender, SMS reminders, waiting time, and chronic conditions that contribute to missed appointments.

---

## 🚀 Project Overview

### **Tools Used**
- Databricks Community Edition  
- Databricks SQL  
- Spark SQL   
- GitHub  

### **Dataset**
- Source: Kaggle Medical Appointment No Show Dataset  
- Rows: 110K  
- Columns: 14  
- Target: `No-show` (Yes/No) → converted into numeric `NoShowFlag`  

---

## 🧼 Data Cleaning & Feature Engineering

### ✔ Converted timestamps  
- `ScheduledDay` → scheduled_date  
- `AppointmentDay` → appointment_date  

### ✔ Calculated new features  
- `wait_days` = days between scheduled & appointment date  
- `NoShowFlag` =  
  - 1 if `No-show` = "Yes"  
  - 0 if `No-show` = "No"  

### ✔ Fixed invalid values  
- Removed negative `Age` records

---

## 🔍 Exploratory Data Analysis (EDA)

### Key Questions Answered:
- Which gender misses more appointments?  
- Do SMS reminders reduce no-shows?  
- Which age groups miss the most appointments?  
- Which neighbourhoods have the highest no-show rates?  
- How does waiting time affect the chance of no-shows?

###SQL queries and results: 


<img width="756" height="403" alt="image" src="https://github.com/user-attachments/assets/d32e8925-7272-4130-a7cd-ecd0a04153a9" />


<img width="625" height="383" alt="image" src="https://github.com/user-attachments/assets/6fdab8b4-fe1c-42e1-a487-ff1bf014ce15" />


<img width="653" height="691" alt="image" src="https://github.com/user-attachments/assets/3a3085ac-905b-4164-b959-c9dddb803114" />


<img width="677" height="412" alt="image" src="https://github.com/user-attachments/assets/49d6a00d-fb9e-4468-9eac-c3ee4126117c" />


<img width="682" height="712" alt="image" src="https://github.com/user-attachments/assets/80fc54bf-a8c6-424f-b00f-3e26577138fd" />


<img width="677" height="415" alt="image" src="https://github.com/user-attachments/assets/634f1eab-1ca6-481f-b343-0282e92241f5" />


<img width="718" height="677" alt="image" src="https://github.com/user-attachments/assets/973efd9f-6e5e-4952-bbf7-16a03c80a322" />



