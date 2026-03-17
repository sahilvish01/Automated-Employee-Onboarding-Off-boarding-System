# Automated-Employee-Onboarding-Off-boarding-System

## 📌 Document: Functional Overview
This project automates the manual HR workflows for onboarding new hires and offboarding departing employees within ServiceNow. By utilizing self-service catalog requests, it eliminates paper-based processes and automatically routes tasks to respective departments (IT, Facilities, Security) based on the request type. The goal is to ensure compliance, transparency, and SLA adherence.

## ⚙️ Document: Technical Blueprint
The system architecture is built purely on ServiceNow native capabilities:
1. **Data Model (Backend):** A custom table `Employee Lifecycle` was created to store transactional data. A custom String field `request_type` was added to handle logical routing.
2. **User Interface (Frontend):** A Record Producer acts as the intake form. Variables (Employee ID, Department, Manager, Request Type) are explicitly mapped (`Map to field`) to the custom table to ensure seamless data flow.
3. **Business Logic (Flow Designer):** A custom Flow triggers upon record creation. 
   - Uses strict `contains` string-matching logic to avoid case-sensitivity errors (e.g., matching 'onboarding').
   - Evaluates the `Request Type`.
   - Automatically generates Catalog Tasks for the IT department (e.g., "Setup Laptop and IT Access").

## 🛠️ Document: Setup Manual & Testing
To deploy and test this system in a new instance:
1. Import the project repository/Update Set into ServiceNow Studio.
2. Navigate to **Service Catalog > Record Producers**.
3. Open the `Employee Onboarding/Offboarding Request` item.
4. Click **Try It** to open the form.
5. Fill in dummy data, select **Onboarding**, and click Submit.
6. Navigate to `task.list` in the filter navigator. Verify that a new task ("New Hire Onboarding - Please setup Laptop...") has been automatically generated at the top of the list.

## Screenshots :
<img width="1232" height="553" alt="cd3504a2-1ef5-490e-b2b8-277d3d8ccfb2" src="https://github.com/user-attachments/assets/bb27bc79-abd5-488a-bf24-932b0a05d814" />
<img width="1245" height="1013" alt="a05e78cb-88c3-444d-bdaf-35aff824c3db" src="https://github.com/user-attachments/assets/323b1c4a-ea35-44bc-8f62-37fc590b615e" />
<img width="1908" height="1019" alt="3b0aa554-4201-451e-8d81-f65eeeacce3f" src="https://github.com/user-attachments/assets/0e67dd24-09ae-4f57-8ff6-09d9d4dd761c" />
<img width="1914" height="340" alt="ec1b631b-8cd1-4bf8-92f9-46d63f6bd809" src="https://github.com/user-attachments/assets/c605207b-5748-49fa-b36f-9ae8313bbda7" />
