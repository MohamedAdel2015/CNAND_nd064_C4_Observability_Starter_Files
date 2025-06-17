**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/installation.PNG)

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Grafana.PNG)

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Basic_Dashboard.PNG)

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

Service Level Indicators (SLIs) are specific, measurable metrics that reflect the performance and reliability of a service from the user's perspective. For an SLO focused on *monthly uptime*, the SLI would be the percentage of time the service is available and operational during the month. For *request response time*, the SLI would measure the proportion of requests that are served within a defined acceptable latency threshold. These SLIs help quantify how well the service meets its reliability and performance objectives.

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

It is important to select metrics that directly reflect the reliability and performance experienced by users. We have our four golden signals which are Latency, Traffic, Errors and Saturation and we can include Availability to them. Here are five detailed metrics to measure the SLIs:

1. **Uptime Percentage (Availability)**
    Measures the proportion of time the service is available and operational within a given period (e.g., monthly). This directly supports the SLI for monthly uptime.

2. **Request Success Rate (Traffic)**  
    Calculates the percentage of successful requests (e.g., HTTP 2xx responses) out of total requests. This helps identify reliability from the user's perspective.

3. **Average Response Time (Latency)**  
    Tracks the mean time taken to respond to user requests. This metric supports the SLI for request response time and helps ensure performance targets are met.

4. **Error Rate (4xx and 5xx) (Errors)**  
    Measures the frequency of client (4xx) and server (5xx) errors. High error rates can indicate issues affecting user experience and service reliability.

5. **Resource Utilization (Saturation)**  
    Measures how much of the system's resources (such as CPU, memory, or network bandwidth) are being used. High saturation levels can lead to degraded performance or downtime, directly impacting the reliability and responsiveness of the service.

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/SLI_Dashboard.PNG)

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Jaeger.PNG)
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Span.PNG)

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Jaeger_Dashboard.PNG)

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name: Mohamed Adel

Date: Tuesday, 17th June 2025

Subject: Trial Service giving 500 Internal Server Error

Affected Area: Trial Microservice

Severity: High

Description:
We always getting 500 Internal Server Error from trial microservice due to below error from Logs:
HTTPSConnectionPool(host='jobs.github.com', port=443): Max retries exceeded with url: /positions.json?description=python (Caused by NewConnectionError('<urllib3.connection.HTTPSConnection object at 0x7fb549828c50>: Failed to establish a new connection: [Errno 111] Connection refused'))

![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Trace-Error.PNG)

## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

1. **Service Uptime Percentage**: Measures the percentage of time the application is available and operational during the month.
2. **Error Rate**: Tracks the proportion of failed requests (e.g., HTTP 4xx & 5xx errors) over total requests.
3. **Request Latency**: Measures the percentage of requests served within a defined acceptable response time.
4. **Successful Request Rate**: Calculates the percentage of successful responses (e.g., HTTP 2xx) out of total requests.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

1. **Daily Uptime KPI**: Tracks the actual uptime percentage each month to ensure it meets or exceeds the 99.95% SLO. This KPI is critical for monitoring service reliability.
2. **Error Rate KPI**: Monitors the rate of 4xx & 5xx errors over time, helping to quickly identify and address backend issues that could impact uptime.
3. **Latency KPI**: Measures the proportion of requests completed within the target response time, ensuring the application remains performant and responsive for users.

These KPIs were chosen because they directly reflect the core objectives of high availability, reliability, and performance, which are essential for meeting the defined SLO.

## Final Dashboard
![](/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Final_Dashboard.PNG)

The final Grafana dashboard includes the following graphs to capture all the KPIs, SLIs, and SLOs:

1. **Monthly Uptime Percentage**: A time series graph showing the uptime of the application over the past month, allowing quick verification against the 99.95% SLO.
2. **Error Rate (4xx & 5xx)**: A stacked bar or line graph displaying the rate of client (4xx) and server (5xx) errors over time, helping to identify periods of increased errors.
3. **Request Latency**: A histogram or percentile graph showing the distribution of request response times, highlighting the percentage of requests meeting the latency SLI.
4. **Successful Request Rate**: A gauge or line graph indicating the proportion of successful (2xx) responses out of total requests.
5. **Resource Utilization**: Additional panels for CPU and memory usage to monitor system saturation and ensure performance.

These graphs provide a comprehensive view of service reliability, availability, and performance, making it easy to track progress toward meeting the defined SLOs and KPIs.
