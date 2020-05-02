# spring-cloud-turbine-repo

Port: 9095

This is a turbine service which will aggregate the health status of all the services.
We would be monitoring the health of services: product-service & user-service

Follow the steps below to run turbine it-
Step 1. Run product-service and user-service
Step 2. Run turbine-stream app
Step 3. Go to http://localhost:9005/hystrix
Step 4. Enter http://localhost:9005/turbine.stream?cluster=default URL and click on "Monitor Stream" 
		OR use http://localhost:9005/hystrix/monitor?stream=http://localhost:9005/turbine.stream?cluster=default URL
Step 5. Start hitting your requests and status will update on the dashboard.

If you want to view the health of one app, then follow steps below 
Step 1 - Step 3 : Same as above
Step 4. Enter http://localhost:8100/hystrix.stream (where 8100 is the port of user-service) and click on "Monitor Stream" 
		OR use http://localhost:9005/hystrix/monitor?stream=http://localhost:8100/hystrix.stream URL


Significance of hystrix commands added in applicaion.properties file of the apps

-> timeoutInMilliseconds: This is the timeout provided for each request. If there's a latency, fallback will be called.
-> requestVolumeThreshold: This is the maximum number of failed consecutive requests allowed. Post which circuit is opened and all following requests to the service are served by fallback
-> sleepWindowInMilliseconds: This is the time for which the circuit is kept open when it breaks.
-> errorThresholdPercentage: This is the threshold percentage of failed requests. Post which circuit is broken. 