# Comprehensive Web Application Performance Testing & Analysis 

Name : Muhammad Hasif Bin Mohamed Suffian  
Matrics no: 2025659274  
Lecturer: Sir Shahadan  
Class: NBCS2555A  

# Objective of the assignment:
To design, execute, and critically analyze a performance test plan for a web application using a specialized testing tool, thereby demonstrating the ability to interpret key performance indicators (KPIs) and document technical findings effectively for a professional audience.
 
# Requirement: 
1.	Performance test tool: Apache Jmeter
2.	Performance test type: Load test, Spike test, Stress test
3.	Target web application: asciiart.artillery.io


# Activity:
# Installing Jmeter on Windows:
1.	https://jmeter.apache.org/download_jmeter.cgi  
use the link above to search for the zip file for the Jmeter application
2.	Download the file that has the name zip for windows and tgz for linux/macOS.
3.	After installing, you can abstract the zip folder to the place that is suitable according to the file path that you have chosen.
4.	There are also a few plugin you can use to add in the Jmeter such as rotating JTL listener and Perfmon (server performance monitoring)
5.	To easily add on plugin you can use plugin manager 
6.	Download the manager from documentation and place the download file into the bin/ext file in jmeter folder.

# Install java (JDK 8 and above)
1.	To use the Jmeter you will need to first install java on your machine. Below is the link to download the java development test kit.
2.	https://www.oracle.com/asean/java/technologies/downloads/#jdk25-windows
3.	After you have done downloading the file you can run and install it on the machine.

For the testing I’m doing this time I will be using the website [http://asciiart.artillery.io] to test whether it is stable or not by doing the load test, stress test and spike test.

# Download the file groovy-xml-3.0.20.zip,oro-2.0.8.zip, xstream-1.4.20.zip and extract these file into one folder name lib

# Hypothesis:
Base on the test that has been conducted on the website the application will remain stable and responsive up to a moderate concurrency threshold of 110 simultaneous users.  After that point, performance degradation will occur due to resource contention in backend services, leading to increase latency, error rate and stagnation.

# Thread group setup:
To execute the test first you will need to open the Jmeter and create new work/template, then add a new thread group and name it according to the test that you want to perform. After that select the thread group and remark it as load test, stress test and spike test to easily analyse the information. The time that I will use to run the test is 30 minutes for load test and the stress test while I’m going to use around 5 minutes to run the spike test to measure the server capacity to handle sudden spike when it is in use by a lot of user at one time. After done with setting up the load type, duration, and user thread quantity for each of the test we will need to create a new path for the output file to be save in. For this test I will be saving it in my folder name load-stress and spike-report.

# Step to installing plugin:
1.	Open the page Jmeter plugin and select documentation. 
https://jmeter-plugins.org/.
2.	Scroll down and select jar files that are written in hyperlink.
3.	Search for the jar file in download folder and put it into Jmeter folder name lib/ext. 
4.	Open the Jmeter application and select Options.
5.	Select plugin manager.
6.	Select available Plugins.
7.	Select custom thread group.
8.	Press installs and restarts the Jmeter application.  
#you can add any plugins available that you want to use from the manager by installing it.
# Step to set ultimate thread for spike test:
1.	From the Test plan option select add
2.	Select thread user
3.	Select jp@gc - ultimate thread group
4.	On the right-hand side box, you can change the name
5.	From the thread schedule you can input the number of thread count(user) 
6.	Add row and put the number of spike users.
7.	Set the start thread count, initial delay, startup time, hold load for and shutdown time according to your test need.
The graph helps you visualize the load pattern - critical for understanding how your system will be stressed.

Notes: 
Start Threads Count - Number of virtual users (threads) to launch for this schedule row.
Initial Delay - Time to wait before starting the first thread (after test begins).
Startup Time - Time over which all threads ramp up gradually (not all at once). 
Hold Load For - Duration during which all threads stay active and generate load. 
Shutdown Time - Time over which threads ramp down (graceful exit, not instant stop).

# Step to add sampler(http):  
1.	Right click on the thread group.
2.	Select add.
3.	Select sampler. 
4.	Select HTTP request.
5.	Go back to thread and select HTTP request under the thread group name.
6.	On the right you can see the HTTP request box where you can change the box name.
7.	Select server name or IP and write in the server name that you want to test.
8.	For example, I will use the server name asciiart.artillery.io.
9.	From the selection box I will use the GET function to retrieve data from the server.
10.	Lastly, you can select any path that your data will be retrieved if you have multiple pages to test in your project.

# Step to view your run test:   
1.	Right click the thread group.
2.	Select add.
3.	Select listener.
4.	Select view results tree – to view the status of HTTP request that being send from your device to the server.
5.	Repeat step 1 and 2.
6.	Add the summary reports – to view the summary of your report which consist of:-
-	Label - name of the sampler.
-	Samples - total number of requests sent for that sampler.
-	Average - average response time for all samples (in milliseconds).
-	Min - minimum response time recorded.
-	Max - maximum response time recorded.
-	Std. Dev. - standard deviation of response time (shows variability). 
-	Error % - percentage of requests that failed.
-	Throughput - request per second (depending on unit).
-	Received KB/sec - amount of data received from the server per second.
-	Sent KB/sec - amount of data sent to the server per second.
-	Average Bytes - average size of the response data.

7.	Add the jp@gc-active threads over time - a graph listener that comes from the plugin set. Use to visualize how the number of active threads changes during the test execution.
8.	Add the simple data writer - to log raw results to a file .eg .csv/.jtl format file (this file is for non-GUI report).

# Step to save your report:   
1.	After the run that you have done is finished select the tools on the upper taskbar.
2.	Select Generate HTML report.
3.	On the first row you can choose the location that you want to save the.
Notes: you must create a file in csv/jtl format first and choose it in the browse list.
4.	On the second row is the user properties file, select the user file from the folder bin/user.properties.
5.	On the third row select the folder that you want the output folder which consists of the index.html.
6.	After done filling all the row click generate report and you can see the output folder in the file location that you have chosen.

The result of the test is as shown below which is from the graph.


# Test result
# Load test
The first test that I will do is load test which is to check the stability of the website when a few users enter the page. So, by doing the test you can see the response time and stability when there are a few people log in to the website. The scope is to run under normal operating condition, and the outcome is to see the throughput, latency, and resource usage. The function is to avoid failure from happening on a running website.
From the test we can see that the website is stable and able to maintain its connection when there are 1000 users in the website in 5 minutes. After load test is done the threads gradually stop sending requests.  
<img width="326" height="233" alt="Image" src="https://github.com/user-attachments/assets/8964f869-4ad4-453d-95d1-df3976916e9d" />

 

# Stress test
The second test is the stress test where we will check the website capability when handling a lot of users under extreme load. The scope of the test is to operate beyond normal limits and to see the stability, error handling and recovery of the website. This test is to observe failure and recovery of the website.
In this test you can see that the average response time is reduced when it reaches 755 ms and starts to recover back and get to 720+. At that point the web fluctuates, drops then stabilizes, indicating a recovery or optimization event.  
<img width="319" height="226" alt="Image" src="https://github.com/user-attachments/assets/f777dc20-e2d1-4763-832c-59eb40a6cda3" />
 

# Spike test
The third test that we will perform is the spike test which will assess the website performance when the system suddenly subjected to a sharp, extreme increase in load to evaluate how it reacts to abrupt traffic change. The main purpose is to see whether the website can handle the sudden burst of traffic without crashing, slow down excessively or corrupting data. 
Here we can see that the graph fall drastically showing that the response drop due to the spike test that is perform which has shock the server and causing the response time to drop by a lot after a few second the request has recover showing that this is the bottleneck for the website. After the sudden shock the response time continue to grow increase and maintain back its stability to the original response over time.  
<img width="327" height="245" alt="Image" src="https://github.com/user-attachments/assets/3caa3f74-588b-4956-8c60-ecd80f004434" /> 

 
# Conclusion:
# Load test and stress test
The system is functionally stable with minimal errors.However, latency hotspots in the "Home" and "HTTP Request" endpoints indicate performance bottlenecks under load. These should be targeted for profiling and optimization, especially if user experience or SLA thresholds demand sub-500 ms response times.

# Spike test 
The spike test successfully revealed critical performance weaknesses in the "HTTP Request" endpoint.  
-	The system can handle high throughput, but latency and error rates spike sharply under sudden load.

# Immediate action should include:  
-	Profiling the failing endpoint
-	Optimizing backend logic
-	Improving error handling and scaling mechanisms






