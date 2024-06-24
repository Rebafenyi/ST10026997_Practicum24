# ST10026997_Practicum24
Practical work
----Question1 ERD

--Instructor
CREATE TABLE Instructor (
    ins_ID NUMBER(5) PRIMARY KEY,
    ins_fname VARCHAR2(100) NOT NULL,
    ins_sname VARCHAR2(100) NOT NULL,
    ins_contact VARCHAR2(20) NOT NULL,
    ins_level NUMBER(2) NOT NULL
);

--Customer
CREATE TABLE Customer (
    cust_id VARCHAR2(5) PRIMARY KEY,
    cust_fname VARCHAR2(100) NOT NULL,
    cust_sname VARCHAR2(100) NOT NULL,
    cust_address VARCHAR2(200) NOT NULL,
    cust_contact VARCHAR2(20) NOT NULL
);

---Dive
CREATE TABLE Dive (
    DIVE_ID NUMBER(5) PRIMARY KEY,
    DIVE_NAME VARCHAR2(100) NOT NULL,
    DIVE_DURATION VARCHAR2(50),
    DIVE_LOCATION VARCHAR2(100),
    DIVE_EXP_LEVEL NUMBER(2),
    DIVE_COST NUMBER(7, 2)
);


---Dive_Event
CREATE TABLE Dive_Event (
    dive_event_id VARCHAR2(10) PRIMARY KEY,
    dive_date DATE NOT NULL,
    dive_participants NUMBER(5),
    ins_ID NUMBER(5) CONSTRAINT fk_ins_ID REFERENCES Instructor(ins_ID),
    cust_id VARCHAR2(5) CONSTRAINT fk_cust_id REFERENCES Customer(cust_id),
    dive_ID NUMBER(5) CONSTRAINT fk_dive_ID REFERENCES Dive(DIVE_ID)
);


-- Inserting into Instructor table
INSERT INTO Instructor (ins_ID, ins_fname, ins_sname, ins_contact, ins_level) VALUES (101, 'James', 'Willis', '0843569851', 7);
INSERT INTO Instructor (ins_ID, ins_fname, ins_sname, ins_contact, ins_level) VALUES (102, 'Sam', 'Wait', '0763698521', 2);
INSERT INTO Instructor (ins_ID, ins_fname, ins_sname, ins_contact, ins_level) VALUES (103, 'Sally', 'Gumede', '0786598521', 8);
INSERT INTO Instructor (ins_ID, ins_fname, ins_sname, ins_contact, ins_level) VALUES (104, 'Bob', 'Du Preez', '0796369857', 3);
INSERT INTO Instructor (ins_ID, ins_fname, ins_sname, ins_contact, ins_level) VALUES (105, 'Simon', 'Jones', '0826598741', 9);

-- Inserting into Customer table
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C115', 'Heinrich', 'Willis', '3 Main Road', '0821253659');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C116', 'David', 'Watson', '13 Cape Road', '0769658547');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C117', 'Waldo', 'Smith', '3 Mountain Road', '0863256574');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C118', 'Alex', 'Hanson', '8 Circle Road', '0762356587');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C119', 'Kuhle', 'Bitterhout', '15 Main Road', '0821235258');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C120', 'Thando', 'Zolani', '88 Summer Road', '0847541254');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C121', 'Philip', 'Jackson', '3 Long Road', '0745556658');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C122', 'Sarah', 'Jones', '7 Sea Road', '0814745745');
INSERT INTO Customer (cust_id, cust_fname, cust_sname, cust_address, cust_contact) VALUES ('C123', 'Catherine', 'Howard', '31 Lake Road', '0822232521');


-- Inserting into Dive table
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (550, 'Shark Dive', '3 hours', 'Shark Point', 8, 500);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (551, 'Coral Dive', '1 hour', 'Break Point', 7, 300);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (552, 'Wave Crescent', '2 hours', 'Ship wreck ally', 3, 800);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (553, 'Underwater Exploration', '1 hour', 'Coral ally', 2, 250);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (554, 'Underwater Adventure', '3 hour', 'Sandy Beach', 3, 750);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (555, 'Deep Blue Ocean', '30 minutes', 'Lazy Waves', 2, 120);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (556, 'Rough Seas', '1 hour', 'Pipe', 9, 700);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (557, 'White Water', '2 hour', 'Drifts', 5, 200);
INSERT INTO Dive (DIVE_ID, DIVE_NAME, DIVE_DURATION, DIVE_LOCATION, DIVE_EXP_LEVEL, DIVE_COST) VALUES (558, 'Current Adventure', '2 hour', 'Rock Lands', 3, 150);





-- Inserting into Dive_Event table
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_101', TO_DATE('2017-07-15', 'YYYY-MM-DD'), 5, 103, 'C115', 558);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_102', TO_DATE('16-Jul-17', 'DD-Mon-YY'), 7, 102, 'C117', 555);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_103', TO_DATE('18-Jul-17', 'DD-Mon-YY'), 8, 104, 'C118', 552);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_104', TO_DATE('19-Jul-17', 'DD-Mon-YY'), 3, 101, 'C119', 551);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_105', TO_DATE('21-Jul-17', 'DD-Mon-YY'), 5, 104, 'C121', 558);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_106', TO_DATE('22-Jul-17', 'DD-Mon-YY'), 8, 105, 'C120', 556);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_107', TO_DATE('25-Jul-17', 'DD-Mon-YY'), 10, 105, 'C115', 554);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_108', TO_DATE('27-Jul-17', 'DD-Mon-YY'), 5, 101, 'C122', 552);
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID) VALUES ('de_109', TO_DATE('28-Jul-17', 'DD-Mon-YY'), 3, 102, 'C123', 553);


Select * from Instructor;
Select * from Customer;
Select * from Dive;
Select * from Dive_Event;

----Question2

--Question 2

--Admin
CONNECT sys as sysdba;

-- Create the administrator role
CREATE ROLE admin_role;

-- Grant necessary privileges to the administrator role
GRANT CONNECT TO admin_role;
GRANT RESOURCE TO admin_role;
GRANT DBA TO admin_role;

-- Create the administrator user and assign the role
CREATE USER admin_user IDENTIFIED BY admin_password;
GRANT admin_role TO admin_user;

--GENERAL USER OF THE SYSTEM

CONNECT sys as sysdba;

-- Create the general user role
CREATE ROLE general_role;

-- Grant specific privileges to the general user role
GRANT CONNECT TO general_role;
GRANT SELECT ON your_schema.your_table TO general_role;
GRANT INSERT ON your_schema.your_table TO general_role;
GRANT UPDATE ON your_schema.your_table TO general_role;
GRANT DELETE ON your_schema.your_table TO general_role; 

Optionally, grant specific privileges on more tables or schemas
GRANT SELECT, INSERT, UPDATE, DELETE ON another_schema.another_table TO general_role;

-- Create the general user and assign the role
CREATE USER general_user IDENTIFIED BY general_password;
GRANT general_role TO general_user;



----Question3
SELECT 
    i.ins_fname || ', ' || i.ins_sname AS INSTRUCTOR,
    c.cust_fname || ', ' || c.cust_sname AS CUSTOMER,
    d.dive_location AS DIVE_LOCATION,
    de.dive_participants AS DIVE_PARTICIPANTS
FROM 
    Dive_Event de
JOIN 
    Customer c ON de.cust_id = c.cust_id
JOIN 
    Instructor i ON de.ins_ID = i.ins_ID
JOIN 
    Dive d ON de.dive_ID = d.dive_ID
WHERE 
    de.dive_participants BETWEEN 8 AND 10;


---Question4-------------------------------
SET SERVEROUTPUT ON;

DECLARE
    v_dive_name Dive.dive_name%TYPE;
    v_dive_date Dive_Event.dive_date%TYPE;
    v_dive_participants Dive_Event.dive_participants%TYPE;
    
    CURSOR dive_cursor IS
        SELECT 
            d.dive_name,
            de.dive_date,
            de.dive_participants
        FROM Dive_Event de
        JOIN Dive d ON de.dive_ID = d.dive_ID
        WHERE 
            de.dive_participants >= 10;
    
    
    
BEGIN
    OPEN dive_cursor;
    LOOP
        FETCH dive_cursor INTO v_dive_name, v_dive_date, v_dive_participants;
        EXIT WHEN dive_cursor%NOTFOUND;
        
        DBMS_OUTPUT.PUT_LINE('DIVE NAME: ' || v_dive_name);
        DBMS_OUTPUT.PUT_LINE('DIVE DATE: ' || TO_CHAR(v_dive_date, 'DD/MON/YYYY'));
        DBMS_OUTPUT.PUT_LINE('PARTICIPANTS: ' || v_dive_participants);
        DBMS_OUTPUT.PUT_LINE('------------------------------');
        
    END LOOP;
    CLOSE dive_cursor;
END;
/


---Question5------------
SET SERVEROUTPUT ON;

SET SERVEROUTPUT ON;

DECLARE
    v_customer_name Customer.cust_fname%TYPE;
    v_dive_name Dive.dive_name%TYPE;
    v_dive_participants Dive_Event.dive_participants%TYPE;
    v_dive_cost Dive.dive_cost%TYPE;
    v_instructors_required NUMBER(1);
    
    CURSOR dive_cursor IS
        SELECT 
            c.cust_fname || ', ' || c.cust_sname AS customer_name,
            d.dive_name,
            de.dive_participants,
            d.dive_cost
        FROM 
            Dive_Event de
        JOIN 
            Customer c ON de.cust_id = c.cust_id
        JOIN 
            Dive d ON de.dive_ID = d.dive_ID
        WHERE 
            d.dive_cost > 500;
BEGIN
    OPEN dive_cursor;
    LOOP
        FETCH dive_cursor INTO v_customer_name, v_dive_name, v_dive_participants, v_dive_cost;
        EXIT WHEN dive_cursor%NOTFOUND;
        
        -- Determine the number of instructors required based on participants
        IF v_dive_participants <= 4 THEN
            v_instructors_required := 1;
        ELSIF v_dive_participants BETWEEN 5 AND 7 THEN
            v_instructors_required := 2;
        ELSE
            v_instructors_required := 3;
        END IF;
        
        -- Output the results
        DBMS_OUTPUT.PUT_LINE('CUSTOMER: ' || v_customer_name);
        DBMS_OUTPUT.PUT_LINE('DIVE NAME: ' || v_dive_name);
        DBMS_OUTPUT.PUT_LINE('PARTICIPANTS: ' || v_dive_participants);
        DBMS_OUTPUT.PUT_LINE('STATUS: ' || v_instructors_required || ' instructors required.');
        DBMS_OUTPUT.PUT_LINE('--------------------');
    END LOOP;
    
    -- Display the number of rows processed using %ROWCOUNT
    DBMS_OUTPUT.PUT_LINE('Total rows processed: ' || dive_cursor%ROWCOUNT);
    
    CLOSE dive_cursor;
END;
/

---Question6
CREATE VIEW Vw_Dive_Event AS
SELECT
    de.ins_ID AS INS_ID,
    de.cust_id AS Cust_id,
    c.cust_address AS Cust_Address,
    d.DIVE_DURATION AS Dive_duration,
    TO_CHAR(de.dive_date, 'DD/MON/YY') AS Dive_date
FROM
    Dive_Event de
JOIN
    Customer c ON de.cust_id = c.cust_id
JOIN
    Dive d ON de.dive_ID = d.DIVE_ID
WHERE
    de.dive_date < TO_DATE('2017-07-19', 'YYYY-MM-DD');


SELECT *
FROM Vw_Dive_Event
WHERE INS_ID = 104
  AND Cust_id = 'C118'
  AND Cust_Address = '8 Circle Road'
  AND Dive_duration = '2 hours'
  AND Dive_date = '18/JUL/17';



---Question7
CREATE OR REPLACE TRIGGER New_Dive_Event
BEFORE INSERT ON Dive_Event
FOR EACH ROW
DECLARE
    v_participants NUMBER;
BEGIN
    v_participants := :NEW.dive_participants;
    
    IF v_participants <= 0 OR v_participants > 20 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Participants must be between 1 and 20.');
    END IF;
END;
/
---Test Codes
-- Valid insert (10 participants)
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID)
VALUES ('de_test1', SYSDATE, 10, 101, 'C115', 550);

-- Invalid insert (0 participants)
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID)
VALUES ('de_test2', SYSDATE, 0, 102, 'C117', 551);

-- Invalid insert (21 participants)
INSERT INTO Dive_Event (dive_event_id, dive_date, dive_participants, ins_ID, cust_id, dive_ID)
VALUES ('de_test3', SYSDATE, 21, 103, 'C118', 552);



SELECT * FROM Dive_Event;

----Question8
CREATE OR REPLACE PROCEDURE sp_Customer_Details (
    p_cust_id IN Customer.cust_id%TYPE,
    p_dive_date IN DATE
)
IS
    v_customer_name VARCHAR2(200);
    v_dive_name Dive.dive_name%TYPE;
BEGIN
    -- Query to retrieve customer and dive details
    SELECT 
        c.cust_fname || ' ' || c.cust_sname,
        d.dive_name
    INTO 
        v_customer_name,
        v_dive_name
    FROM 
        Dive_Event de
        JOIN Customer c ON de.cust_id = c.cust_id
        JOIN Dive d ON de.dive_ID = d.DIVE_ID
    WHERE 
        de.cust_id = p_cust_id
        AND de.dive_date = p_dive_date;
    
    -- Display the result
    DBMS_OUTPUT.PUT_LINE('CUSTOMER DETAILS: ' || v_customer_name || ' booked for ' || v_dive_name || ' on ' || TO_CHAR(p_dive_date, 'DD/MON/YY'));
    
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No customer found for the given ID and dive date.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END sp_Customer_Details;
/


SET SERVEROUTPUT ON;

BEGIN
    sp_Customer_Details('C115', TO_DATE('2017-07-15', 'YYYY-MM-DD'));
END;
/

---Question9

CREATE OR REPLACE FUNCTION calculate_monthly_revenue (
    p_month IN VARCHAR2 
)
RETURN NUMBER
IS
    v_total_revenue NUMBER := 0;
BEGIN
    -- Calculates the total revenue for the specified month
    SELECT 
        NVL(SUM(d.DIVE_COST), 0)
    INTO 
        v_total_revenue
    FROM 
        Dive_Event de
        JOIN Dive d ON de.dive_ID = d.DIVE_ID
    WHERE 
        TO_CHAR(de.dive_date, 'MM') = p_month;

    -- Returns the calculated total revenue
    RETURN v_total_revenue;
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        -- Handle case where no dive events are found for the given month
        RETURN 0;  -- Return 0 if no data is found
    WHEN OTHERS THEN
        -- Handle other exceptions
        RETURN NULL;  -- Return NULL for any other exception
END calculate_monthly_revenue;
/


---Question10
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;

public class ITGearDealerGUI extends JFrame {

    // GUI components
    private JComboBox<String> functionComboBox;
    private JTextField customerIdField;
    private JTextField diveDateField;
    private JTextArea resultTextArea;

    // Database connection parameters
    private static final String DB_URL = "jdbc:oracle:thin:@your_host:your_port:your_service_name";
    private static final String DB_USERNAME = "your_username";
    private static final String DB_PASSWORD = "your_password";

    // Constructor
    public ITGearDealerGUI() {
        super("IT Gear Dealer Management");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(500, 400);
        setLocationRelativeTo(null);

        // Function selection panel
        JPanel functionPanel = new JPanel();
        JLabel selectLabel = new JLabel("Select Function:");
        functionComboBox = new JComboBox<>();
        functionComboBox.addItem("sp_customer_details");
        functionComboBox.addItem("fn_Dive_Adjustments");
        functionPanel.add(selectLabel);
        functionPanel.add(functionComboBox);

        // Input panel
        JPanel inputPanel = new JPanel(new GridLayout(2, 2, 10, 10));
        inputPanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));
        inputPanel.add(new JLabel("Customer ID:"));
        customerIdField = new JTextField(10);
        inputPanel.add(customerIdField);
        inputPanel.add(new JLabel("Dive Date:"));
        diveDateField = new JTextField(10);
        inputPanel.add(diveDateField);

        // Execute and clear buttons
        JPanel buttonPanel = new JPanel();
        JButton executeButton = new JButton("Execute");
        executeButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                executeSelectedFunction();
            }
        });
        JButton clearButton = new JButton("Clear");
        clearButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                resultTextArea.setText("");
            }
        });
        buttonPanel.add(executeButton);
        buttonPanel.add(clearButton);

        // Result area
        JPanel resultPanel = new JPanel(new BorderLayout());
        resultPanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));
        resultPanel.add(new JLabel("Result Area:"), BorderLayout.NORTH);
        resultTextArea = new JTextArea(10, 40);
        resultTextArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(resultTextArea);
        resultPanel.add(scrollPane, BorderLayout.CENTER);

        // Main frame setup
        setLayout(new BorderLayout());
        add(functionPanel, BorderLayout.NORTH);
        add(inputPanel, BorderLayout.CENTER);
        add(buttonPanel, BorderLayout.SOUTH);
        add(resultPanel, BorderLayout.SOUTH);
    }

    // Method to execute selected function based on user input
    private void executeSelectedFunction() {
        String selectedFunction = (String) functionComboBox.getSelectedItem();
        String customerId = customerIdField.getText().trim();
        String diveDate = diveDateField.getText().trim();

        if (selectedFunction.equals("sp_customer_details")) {
            executeSpCustomerDetails(customerId, diveDate);
        } else if (selectedFunction.equals("fn_Dive_Adjustments")) {
            executeFnDiveAdjustments();
        }
    }

    // Method to execute sp_customer_details stored procedure
    private void executeSpCustomerDetails(String customerId, String diveDate) {
        try {
            // Establish database connection
            Connection conn = DriverManager.getConnection(DB_URL, DB_USERNAME, DB_PASSWORD);

            // Prepare SQL call for stored procedure
            String sql = "{ call sp_customer_details(?, ?, ?) }";
            CallableStatement stmt = conn.prepareCall(sql);

            // Set parameters
            stmt.setString(1, customerId);
            stmt.setString(2, diveDate);
            stmt.registerOutParameter(3, Types.VARCHAR); // Assuming the stored procedure returns a VARCHAR result

            // Execute the stored procedure
            stmt.execute();

            // Get and display the result
            String result = stmt.getString(3);
            resultTextArea.setText(result);

            // Close statement and connection
            stmt.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(this, "Error executing stored procedure: " + e.getMessage(),
                    "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    // Method to execute fn_Dive_Adjustments function
    private void executeFnDiveAdjustments() {
        // Placeholder for function execution logic
        // Implement according to your specific function requirements
        JOptionPane.showMessageDialog(this, "Function fn_Dive_Adjustments execution placeholder.",
                "Placeholder", JOptionPane.INFORMATION_MESSAGE);
    }

    // Main method to launch the GUI
    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                ITGearDealerGUI gui = new ITGearDealerGUI();
                gui.setVisible(true);
            }
        });
    }
}

