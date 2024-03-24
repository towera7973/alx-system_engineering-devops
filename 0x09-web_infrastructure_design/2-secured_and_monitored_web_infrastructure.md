
## Specifics About This Infrastructure

The purpose of the firewalls;

for protecting the network (web server)by only providing access to authorized users and  acting as an intermediary between the internal network and the external network and blocking the incoming traffic matching the aforementioned criteria. 

Why is the traffic served over HTTPS
HTTPS is a secure version of the HTTP protocol, which is the protocol used to transfer data over the web. When a website uses HTTPS, it means that all communication between the web server and the client’s web browser is encrypted and secure. This is important for a number of reasons, including protecting the privacy of users’ personal information and preventing attackers from intercepting and altering the data that is transmitted between the server and the client. Additionally, because HTTPS provides a secure connection, it helps to ensure the integrity of the data that is transmitted, which is important for ensuring that the information on a website is accurate and up-to-date.
The purpose of the SSL certificate.

The SSL certificate is for encrypting the traffic between the web servers and the external network to prevent man-in-the-middle attacks (MITM) and network sniffers from sniffing the traffic which could expose valuable information. The SSL certs ensure privacy, integrity, and identification.

whats  monitoring used for
For monitoring the servers and the external network. 

How the monitoring tool is collecting data

They analyse the performance and operations of the servers, measure the overall health, and alert the administrators if the servers are not performing as expected. The monitoring tool observes the servers and provides key metrics about the servers' operations to the administrators. Some common types of monitoring tools include network monitoring tools, server monitoring tools, application performance monitoring tools, and website monitoring tools. These tools can be used to monitor a wide range of metrics, including availability, latency, throughput, error rates, and more

what to do if you want to monitor your web server QPS
To moniter queries per second of website .conduct a few things .
1. Select Monitoring Tools:
Choose a monitoring tool or platform that allows you to track and analyze server metrics, including QPS. Popular options include:

 A. Prometheus: A monitoring and alerting toolkit with a powerful query language (PromQL).
 B.Grafana: A visualization and monitoring tool that can integrate with Prometheus for data visualization.
 C.Datadog: A cloud monitoring platform that offers various monitoring capabilities, including server performance metrics.

2. INstall the application 
 This agent collects system-level metrics, application metrics, and other relevant data.
3. configure them on your web server.involve setting up monitoring for HTTP requests, analyzing access logs, or utilizing built-in features of the monitoring tool to track request rates. Then, you can use their respective dashboards or APIs to monitor your web server’s QPS in real-time
4. Analyze and Optimize:
Regularly analyze the QPS data to identify performance bottlenecks, optimize resource allocation, and make informed decisions about scaling resources or implementing performance improvements.

## Issues With This Infrastructure

+to begin with Terminating SSL at the load balancer means that the load balancer must handle the SSL/TLS encryption and decryption process for incoming HTTPS requests. This can significantly increase the CPU usage and resource utilization of the load balancer, especially in high-traffic environments or when dealing with a large number of SSL connections. Terminating SSL at the load balancer level would leave the traffic between the load balancer and the web servers(backend especially the application server ) unencrypted because the ssl will be invalid.

+ Having one MySQL server is an issue because it is not scalable and can act as a single point of failure for the web infrastructure.
+ Having servers with all the same components would make the components contend for resources on the server like CPU, Memory, I/O, etc., which can lead to poor performance and also make it difficult to locate the source of the problem. A setup such as this is not easily scalable. 
