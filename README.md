
# vNextelecom Survey App Guide

vNextelecom is a call center management system that provides real-time analytics and reporting through two main interfaces: the Dashboard and Reports section.
This guide provides a step-by-step walkthrough and run the vNextelecom Survey application on other's system.

---

## Prerequisites

Ensure the following tools and dependencies are installed on the user's system:

1. **Python**: Version 3.8 or higher.
3. **Database**: MySQL.
5. **Required Python Dependencies**:
   - Install dependencies from the `requirements.txt` file:
     ```bash
     pip install -r requirements.txt
     ```
---

## Step 1: Set Up a Virtual Environment

1. Create a virtual environment:

   ```bash
   python -m venv venv
   ```

2. Activate the virtual environment:
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

---

## Step 2: Configure the MySQL Database

1. Log in to your MySQL server:

   ```bash
   mysql -u root -p
   ```

2. Create a new database:

   ```sql
   CREATE DATABASE vnex;
   ```

3. Create a new user and assign a password:

   ```sql
   CREATE USER 'vnex_user'@'localhost' IDENTIFIED BY '123456';
   ```

4. Grant the user access to the database:

   ```sql
   GRANT ALL PRIVILEGES ON vnex.* TO 'vnex_user'@'localhost';
   ```

5. Update the `DATABASES` configuration in the `settings.py` file:

   ```python
   DATABASES = {
       "default": {
           "ENGINE": "django.db.backends.mysql",
           "NAME": "vnex",
           "USER": "vnex_user",
           "PASSWORD": "123456",
           "HOST": "localhost",  # Or your MySQL server's host
           "PORT": "3306",  # Default MySQL port
       }
   }
   ```

6. Apply the database migrations:

   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

---

## Step 4: Create a Superuser

1. Run the following command to create an admin account:

   ```bash
   python manage.py createsuperuser
   ```

2. Follow the prompts to enter the username, and password.

---

## Step 5: Run the Server

1. Start the server:

   ```bash
   python manage.py runserver
   ```

2. Access the application in a web browser at:

   ```
   http://127.0.0.1:8000
   ```

---

## 
## Step 6: Admin Panel Access, User Management, and Queue Assignment

### 1. Access the Admin Panel

1.  Open a web browser and visit:
    
    ```
    http://127.0.0.1:8000/admin
    
    ```
    
3.  **Login**:
    
    -   Use your superuser credentials. 

----------

### 2. Adding Users via the Admin Panel

1.  After logging in, navigate to the **Users** section in the admin panel.
2.  Save the user. 
3.  Choose privillage:
    -   after adding the user ,Optionally, assign superuser status by checking:
        -   **Superuser status** (for full permissions)
        - save the user.

----------

### 3. Creating Queues and Assigning Users

1.  Go to the **Queues** section in the admin panel.
    
2.  Click **Add Queue**:
    -   Provide the rname of the queue.
3.  **Assign Users**:
    -   Use the user selection field in the queue form to assign users who will manage or interact using the queue.
4.  Save the queue.
    
----------
 ### **4. Setting Rate Levels**
 
 1.  Go to the **Levels** section in the admin panel.
    
2.  Click **Add Level**: 
    -   Assagin the rates colums of the data  for rate processing with names such as 
      ( rate1,rate2,rate3 )  in one level for all the levels .
3.  Save the levels.

### 5. Running the Server and Accessing the App

   1.  Access the application at:  http://127.0.0.1:8000
      
   2.  Login View:
         When accessing the app, the user will first see the **Login View**.
          Enter valid credentials to log in.
        
   3.  Dashboard View : 
         Once logged in, the user will be redirected to the **Dashboard View**.
          The dashboard provides an overview of the application's data .
          
   4. Report view : 
          -   In the navigation bar, the user can access the **Report View**.
          -   The **Report View** displays a table containing today's data filtered to show only the user's assigned queues.
    
        
    
    
    
 
----------

----------
