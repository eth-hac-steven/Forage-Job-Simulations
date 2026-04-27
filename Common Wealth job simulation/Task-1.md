# Task 1
## Here is the background information on your task

As a cyber security generalist at Commonwealth Bank, it is important to be aware of the increasing rate and complexity of financial fraud and the need for effective defence solutions. Financial fraud poses a significant challenge for financial institutions, and it is important for Commonwealth Bank to stay up to date with the latest fraud detection technologies and strategies to minimize risk. Protecting against and responding to fraud is a major responsibility for you and your team. By detecting and stopping fraud, the bank can protect its customers, employees and reputation while also enhancing the resilience of its financial system.

To help with this task, you will be using a tool called Splunk to visually represent the given data. Representing data in a visual format, also known as data visualization, makes it easier for the data analytics team to understand and gain insights. Visual data is a universal, fast and effective way to communicate information.

You will be building a dashboard to make it easier to identify patterns and trends in the given dataset. The dashboard will provide crucial reporting and metrics information that can aid in identifying and detecting fraud. By using this dashboard, the team will be able to quickly identify any suspicious activity and take the necessary steps to prevent fraud from occurring. Overall, the goal of this task is to use data visualization and a dashboard to make it easier to detect fraud and protect Commonwealth Bank and its customers from financial loss.  
  
**About the dataset**  
Data was collected and structured by the Fraud team. This dataset consists of payments from various customers made in different periods and amounts. The feature columns include:

- **Step:** This feature represents the month from the start of the simulation. The steps represent four months that the simulation ran virtually.
    - 0: May
    - 1: June
    - 2: July
    - 3: August
- **Customer:** Customer ID
- **Age:** Categorised age
    - 0.0: <= 18
    - 1.0: 19 - 25
    - 2.0: 26 - 35
    - 3.0: 36 - 45
    - 4.0: 46 - 55
    - 5.0: 56 - 65
- **Gender:** Gender of the customer
    - F: Female
    - M: Male
- **PostcodeOrigin:** The postcode of origin/source.
- **Merchant:** The merchant's ID. 
- **Category:** Category of the purchase. 
- **Amount:** Amount of the purchase.
- **Fraud:** Target variable that shows if the transaction is fraudulent - 1 or non-fraudulent - 0.

# Task 1: Data analysis
###   Here is your task

 Your first task is to analyze and visualize the data you have prepared in a software tool called Splunk. Here are the steps you need to take:
    
1. Download the 60-day free trial of Splunk Enterprise. 
    https://www.splunk.com/en_us/download/splunk-enterprise.html
    
    ![splunk-webpage](images/Pasted%20image%2020260413122949.png)


After filling in the content of the form you would be sent an email asking you to verify your email , verify and  download  the appropriate version  for your Operating System.

2. Install Splunk Enterprise on your computer.
    ![installing-splunk](images/Screenshot%202026-04-12%20225544%201.png)

    click next

    ![installing-splunk-2](images/Screenshot%202026-04-12%20225602.png)

    Enter a username and a password

    then wait for the installation to finish
    then click finish which should take you to your browser with this page 	
![splunk-dashboard](images/Pasted%20image%2020260413125153.png)
 Then login using the Credentials created earlier.<br>

 Welcome to your dashboard
 ![splunk-dashboard](images/Screenshot%202026-04-13%20105417.png)

   
3. Using the **“prepared_data”** file in the Resources section, import this file into Splunk. 
   
Step 1:  To do this click on "Add data" on the dashboard page.

![splunk-add-data](images/splunk-setup-add-data.png)
 
Step 2 : then click "upload"  and move to the next page

![uploading-the-data](images/Screenshot%202026-04-13%20105434.png)

Step 3 : On the upload page 
   
 1. click on select file and navigate  to where you downloaded the CSV file to can click open.
   
 2. then click on next.
   
   ![uploading-the-data](images/Pasted%20image%2020260413132630.png)
    
 3. after clicking next , if you see something like this follow this step to correct it  if not skip this;
   
 ![uploading-the-data](images/Pasted%20image%2020260413132950.png)
   
 It means the file is in a wrong format, when downloading the file it may be in xlsx (excel) although it says .CSV as the file extension.

 To resolve this and get the right value open the **"prepared_data.xlsx"** file in Excel and "save as" prepared_data .CSV  then reupload the file the same way.

 4. The image below contains the right value that should be displayed.

 ![uploading-the-data](images/Screenshot%202026-04-13%20120914.png)

  5. Under the timestamp session change it from  **"Auto"** to **"Current time"** by clicking on them.  


6. Then click on **“SaveAs”**. You can name this “fraud_dectection.csv” and save.

![uploading-the-data](images/Pasted%20image%2020260413134819.png)

 7. Click on **“Next”** until you get the result below.

![uploading-the-data](images/Pasted%20image%2020260413134947.png)

4. Study the file using the **“Interesting Fields”** section in Splunk. This tells you about the data you’re using.

 Step 1 : Click on **“Start Searching”** to start analyzing. On the left, you can find the **“Interesting Fields”** section.

 ![uploading-the-data](images/Pasted%20image%2020260413135614.png)
    
5. Create a dashboard to include the following charts/tables:

    1. Count by Category, Fraudulent transactions, Age and Merchant.

 ```  
        sourcetype="Fraud_dectection.csv" fraud="1"
        | stats count by gender, category
        | sort -count
  ```

  ![uploading-the-data](images/Pasted%20image%2020260413192548.png)

 2. Fraud detected by Age, Category, Step (month) and Gender.

 ```  
 sourcetype="Fraud_dectection.csv" fraud="1"
 | stats count by gender, category
 | sort -count
 ```

![uploading-the-data](images/Pasted%20image%2020260413192812.png)

 3. Which gender performed the most fraudulent activities and in what category?  

     using the command below we are able to identify that the Females  committed 49 fraudulent acts in the ES_transportation category.

        ```  
        sourcetype="Fraud_dectection.csv" fraud="1"
        | stats count by gender, category
        | sort -count
        ```
     ![uploading-the-data](images/Pasted%20image%2020260413164438.png)
4.  Which age group performed the most fraudulent activities and to what merchant?
        ![uploading-the-data](images/Pasted%20image%2020260413193357.png)

3. Export the dashboard as a PDF and upload it below as your submission for this task