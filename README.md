# Splunk Project: Monitoring a Critical Server

## Objective

Set up Splunk to monitor a critical server (Windows or Linux) and create a dashboard to visualize key metrics and security events.

### Skills Learned

- Log Collection: Configuring Splunk to collect logs from the critical server, including system, security, and application logs.
- Real-Time Monitoring: Setting up real-time monitoring for key performance indicators (KPIs) such as CPU usage, memory usage, and disk space.
- Alert Configuration: Creating alerts for critical security events, such as failed login attempts, unauthorized access, and service failures.
- Dashboard Creation: Designing a Splunk dashboard that visualizes performance metrics and security events, providing actionable insights.

### Tools Used

- Splunk Universal Forwarder: For collecting and forwarding logs from the critical server to Splunk.
- Splunk Enterprise: To analyze the collected logs, configure alerts, and create dashboards.
- Windows/Linux Server: The critical server being monitored, providing system logs, performance metrics, and security events.

### Outcome
This project successfully demonstrated the ability to monitor a critical server using Splunk. The dashboard provided real-time insights into the server's performance and security status, enabling proactive monitoring and rapid response to potential issues. Key achievements included configuring log collection, setting up alerts for critical events, and creating a comprehensive dashboard to visualize the data. The project highlighted skills in log management, real-time monitoring, and data visualization within a cybersecurity context.

## Steps

Insert our test data and then filter out the data to show the index(Test Data) and the src_ip which in htis case will be our crtical web server we are monitoring

![Screenshot 2024-08-27 213315](https://github.com/user-attachments/assets/7d85b8b6-4353-4e56-82d9-0e36aa6bbda1)

![Screenshot 2024-08-27 213340](https://github.com/user-attachments/assets/20304da5-d87b-45af-9f78-0b168cbc401a)

-----------------------------------------------------------------------------------------------------

From here we need to configure a table to view all our important information we want to view for this server

![Screenshot 2024-08-27 214123](https://github.com/user-attachments/assets/911a26f8-8043-49e3-8ed4-f6e3a1d24186)

-----------------------------------------------------------------------------------------------------

We want to view only ports that have a value so we will use the (dest_port=*) in our initial search to ensure that it has a value, we can do the same for (app)

![Screenshot 2024-08-27 214208](https://github.com/user-attachments/assets/4178ec28-f663-4dc7-adda-328953fb33c8)

![Screenshot 2024-08-27 214724](https://github.com/user-attachments/assets/f23c2da0-d257-4e04-9b85-ce5f550f2dae)

-----------------------------------------------------------------------------------------------------

We can now save this search as a preset to easily filter to this exact search

![Screenshot 2024-08-27 215418](https://github.com/user-attachments/assets/405a227e-1356-4752-b5b9-a2e622a565c1)

-----------------------------------------------------------------------------------------------------

To narrow down our results from the 20k+ of results we are mainly focused on high volume packets coming to and from the server, so see this we can add the (sort - bytes) filter to sort them from least to greatest by byte size, then to see the top 10 we can use (head 10)

![Screenshot 2024-08-27 220001](https://github.com/user-attachments/assets/634e4217-e684-439f-bab5-9d92002ed6eb)

-----------------------------------------------------------------------------------------------------

Now we want to create an alert for any packet size over 80,000 bytes, as we will be deeming this a suspiscious packet size, insert (search bytes > 80000) to give us only packet sizes larger than the threshold. We then want to configure an email alert to notify a team member anytime this happens 

![Screenshot 2024-08-27 220314](https://github.com/user-attachments/assets/5fdb26fc-b582-4731-b415-80312e7676bf)

![Screenshot 2024-08-27 220726](https://github.com/user-attachments/assets/346bbf0a-89d9-4a13-bd37-eef62332b7bf)

![Screenshot 2024-08-27 220731](https://github.com/user-attachments/assets/4622293a-e11e-41b7-8b4c-20efdd6d9925)

-----------------------------------------------------------------------------------------------------

Now we can create a dashboard and start configuring the search tokens 

![Screenshot 2024-08-27 220926](https://github.com/user-attachments/assets/4ecdf09c-cd5d-44d1-98c2-3a5e3c6e86df)

![Screenshot 2024-08-27 222754](https://github.com/user-attachments/assets/4eb1c25b-49b7-409e-a2b9-bfb4b94db225)

![Screenshot 2024-08-27 222803](https://github.com/user-attachments/assets/f250bb92-0d19-45e0-b1eb-68ca62e83e8f)

-----------------------------------------------------------------------------------------------------

Now test out the search filters to easily search through our logs 

![Screenshot 2024-08-27 222827](https://github.com/user-attachments/assets/bdc448eb-d757-4eba-bac5-8ca3d98bd5aa)

![Screenshot 2024-08-27 223223](https://github.com/user-attachments/assets/45f07588-aa58-4737-bdc6-1a5ab2efb99c)










