# Travel-Management-System

## Overview
The **Travel Management System** is a desktop application designed to manage travel bookings, user accounts, and payment processing. This application allows users to log in, sign up, and make bookings for different travel destinations. It also integrates with payment gateways like Paytm for processing payments.

### Features:
- **User Authentication**: Sign up and login functionality.
- **Tour Booking**: Users can browse and book tours.
- **Payment Integration**: Paytm payment gateway integration for booking payments.
- **Splash Screen**: A visually appealing splash screen with smooth animation.
- **Admin Panel**: Manage user data and tour information (in future versions).

## Technologies Used
- **Java**: Core programming language.
- **Swing**: For building the graphical user interface (GUI).
- **JDBC**: To connect the application with the database.
- **SQL**: For managing user and tour data in a MySQL database.
- **Paytm Payment Gateway**: For processing payments.

## Prerequisites
Before running the application, make sure you have the following:
- **JDK** version 8 or above installed.
- **MySQL** or any other database system with necessary drivers.
- Paytm account credentials for integrating payments.
- 

## Step 1: Clone the Repository

1. **Clone the project repository**:
   - You can clone the repository using Git or manually download the ZIP file.
   - To clone via Git, run the following command in your terminal:

     ```bash
     git clone <repository_url>
     ```

2. **Open the project in your IDE**:
   - After cloning or downloading the project, open the project in your preferred IDE.

## Step 2: Install Required Dependencies

1. **Install MySQL JDBC Driver**:
   - The project connects to MySQL, so you need the MySQL JDBC driver.
   - Download the JDBC driver from [MySQL's official website](https://dev.mysql.com/downloads/connector/j/).
   - Add the JDBC JAR file to your IDE's build path (in the `lib` directory or project dependencies).

2. **Install Additional Libraries**:
   - Make sure any necessary libraries are added to the project (e.g., Java Swing for the GUI components). Most of these are standard in Java, but ensure you have the correct versions.

## Step 3: Set Up the Database

1. **Install MySQL**:
   - To run the project, you need a MySQL database to store user data and travel-related information.
   - You can download and install MySQL from [the official website](https://dev.mysql.com/downloads/installer/).
   - Alternatively, you can use services like [XAMPP](https://www.apachefriends.org/index.html) or [WampServer](https://www.wampserver.com/en/) for easy local server setup that includes MySQL.

2. **Create the Database**:
   - After installing MySQL, open the MySQL Command Line or use a MySQL GUI like [MySQL Workbench](https://dev.mysql.com/downloads/workbench/).
   - Create a new database for the project by running the following SQL command:

     ```sql
     CREATE DATABASE travelmanagementsysystem;
     ```

3. **Create the Tables**:
   - Inside the newly created database, create the necessary tables (`account`, etc.) to store user and travel data.
   - Use the following sample SQL commands to create the required table (ensure the table structure matches the fields used in the Java application):

     ```sql
     CREATE TABLE account (
         id INT PRIMARY KEY AUTO_INCREMENT,
         username VARCHAR(50) NOT NULL,
         name VARCHAR(100) NOT NULL,
         password VARCHAR(50) NOT NULL,
         question VARCHAR(100),
         answer VARCHAR(100)
     );
     ```

4. **Configure Database Connection**:
   - The project connects to the MySQL database via the `Conn` class in the Java code.
   - Ensure that the database credentials (username, password, database name) are correct in the `Conn` class.

     For example:

     ```java
     String url = "jdbc:mysql://localhost:3306/travel_management";
     String username = "root";  // replace with your MySQL username
     String password = "password";  // replace with your MySQL password
     ```

5. **Test Database Connection**:
   - After configuring the connection, run the project to check if the application can connect to the database successfully.
   - If there are any issues with the connection, check the MySQL service, ensure the database is running, and verify that the credentials are correct.

6. **Populate Test Data**:
   - Optionally, you can insert some test data into the `account` table to simulate user login and signup.
   - Example:

     ```sql
     INSERT INTO account (username, name, password, question, answer)
     VALUES ('testUser', 'John Doe', 'password123', 'Your Lucky Number?', '7');
     ```

7. **Verify the Database Integration**:
   - Once the database is set up and running, verify that the Java application is interacting correctly with the database by testing the login and signup features.

## Step 4: Configure Database Connection in the Code

1. **Update Database Credentials**:
   - In the `Conn` class (located in the project folder), update the database credentials to match those of your MySQL installation (i.e., username, password, and database name).
   - Example of how to update the connection code:

     ```java
     public class Conn {
         public Connection c;
         public Statement s;
         public Conn() {
             try {
                 Class.forName("com.mysql.cj.jdbc.Driver");
                 c = DriverManager.getConnection("jdbc:mysql://localhost:3306/travel_management", "root", "password");
                 s = c.createStatement();
             } catch (Exception e) {
                 System.out.println(e);
             }
         }
     }
     ```

2. **Test the Connection**:
   - After making these changes, run the project and check if the login, signup, and other database-related features work as expected.

## Step 5: Compile and Run the Project

1. **Compile the Project**:
   - If you're using an IDE (e.g., Eclipse or IntelliJ IDEA), it will automatically compile the project.
   - If you're using the terminal, navigate to the project directory and compile the Java files using:

     ```bash
     javac -d bin src/*.java
     ```

2. **Run the Project**:
   - After compilation, run the `Splash` class to start the application.

     ```bash
     java travel.management.system.Splash
     ```

3. **Verify Application Features**:
   - Check if all the features of the application are working as expected (login, signup, payment system, etc.).

## Step 6: Test the Application

1. **Verify Front-End and Back-End Interaction**:
   - Ensure that the front-end (GUI) components work properly by testing actions like login, sign-up, and payments.
   - Ensure that the database is correctly receiving and updating data for these actions.

2. **Handle Common Errors**:
   - If you encounter errors related to the MySQL connection, verify the credentials and database setup.
   - For any runtime errors in the Java code, check the error messages in the IDE's console for further debugging.

## Troubleshooting

- **Error: Database Connection Failed**: 
   - Ensure that MySQL is running and the credentials in the `Conn` class are correct.
   - Try using `localhost` or `127.0.0.1` for the database host in the connection string.

- **Error: Missing Libraries**: 
   - Ensure that the MySQL JDBC driver JAR file is included in your project's build path.

- **Error: GUI Not Displaying Properly**: 
   - Make sure you have Java Swing libraries included and are using a compatible Java version.

## Conclusion

Congratulations, you have successfully set up the Travel Management System! You can now use it for travel-related functionalities like booking, payments, and more.

Feel free to contribute or customize the system further as needed.

## Screenshots

Here is a screenshot of the Travel Management System login page:
![Screenshots](https://github.com/Soundarya-Anmole/Travel-Management-System/tree/6a996efd747b8d77803b229cdbcbe98a8eacab56/Screenshots)
