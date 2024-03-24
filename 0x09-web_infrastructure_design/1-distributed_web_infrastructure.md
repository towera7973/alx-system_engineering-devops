Description
The web infrastructure has a primary server, and its  replica , and also a load balancer. The load balancer helps distribute traffic between the primary and replica servers, reducing the load on the primary server. This setup aims to improve performance, reliability, and scalability by sharing the workload across multiple servers and providing redundancy in case one server fails.

Specifics About This Infrastructure

Here, We have added a load balancer and another server, Why?

To distribute incoming traffic across multiple servers to ensure that no single server becomes overwhelmed with requests, which increases the efficiency, reliability, and availability of your site. If one web server crashes, the Load balancer automatically redirects the traffic to the remaining web servers.

The Load Balancer has different algorithms for how it divides up the workload, such as:

Round Robin algorithim — Requests are distributed across the group of servers sequentially. Request 1 is directed to server 1, request 2 to server 2, and so forth.
IP Hash Algorithm — The IP address of the client is used to determine which server the request will be directed to. e.g, all IP addresses from 127.1.0.0–127.24.4.0 will be sent to server 1 and the rest server 2.
Least Connections algorithim — Before redirecting a request to a server, the Load Balancer finds out  which server has the least connections, and then sends the request to there.

How our Load-balancer Enables an active-active or active-passive setup
its as simple as in an active - passive  mode the load balancer send request to one server and the other acts as a redundance,the one that has no traffic is in passive mode  and in active-active all servers are active doing works . the load balancer spreads out the workload’s traffic among multiple nodes.

How a database Primary-Replica (Master-Slave) cluster works
A Primary-Replica setup configures one server to act as the Primary server and the other server to act as a Replica of the Primary server.The master logs the updates,read and write , which then ripple through to the slaves and these are in sync when thr master writes the data.
If the primary server goes down for any reason, one of the replica servers can be promoted to take its place, ensuring that the database remains available and that no data is lost

difference between the Primary node and the Replica node in regard to the application
 primary node is responsible for handling user requests, executing application logic, and managing data modifications, while replica nodes assist by sharing the workload, providing fault tolerance, and ensuring data redundancy.

Issues With This Infrastructure
spof 
No single point of faiure because we have a redundancy .

Security Issues (no firewall, no HTTPS)
Thre is no security in the system ,hackers can attach the system because there is no security certificate issues for authilizaton of users to use the website nlike https .No increpition of mesage and monitering of status
