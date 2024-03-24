specifics about this infrastructure
1. Defining A server 
 a device, a virtual device or computer program or providing functionality for other programs or devices, called “clients/ users”.
2. role of the domain name
DN is translated  into IP addresses via internet.This is when the user types the domain name on the browser .it is human readable and saves as a brad of the webside .

3. www in www.foobar.com is CNAME record 

4. role of the web server
it is resiponsible for handling http reuests from users' browsers.It directly works with html and css for instance and redirects code based applications with python ,node js for instance to apllication server. 

5. role of the application server
This is where the website's codebase resides and is run , it works on processing all dynamic content request like E- commence transaction and interacts with database to  and  generates responses based on user requests.
6. role of the database
it stores website  data in tables and manages it .It collects the data from application server , it can delete ,create , modify ,update the data based on appliction request. 

7. What is the server using to communicate with the computer of the user requesting the website
HTTPS protocal

Issues with this infrastructure

8. SPOF
The system is vulnerble to single point failure since it does not have a backup of servers or database .If one of these failes the whole system fails .

9. Downtime when maintenance needed 
 The wesite will be experiacing downtime during maintenance since we only have one single server ,when it is being maintanine everything needs to be ceased .

10. Cannot scale if there's too much incoming traffic.
if there is too much rquest from the client ,it can not scale because the resource kike storage and processor are also limited to specific requests. 
