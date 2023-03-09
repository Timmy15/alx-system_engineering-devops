# Server requests failure report
The platform experienced a significant outage last week, with all services down and users unable to access the platform routes due to 500 Error responses. The problem was traced back to the master server, web-01, which had failed due to a memory outage. This affected 90% of our users, causing a major disruption to their daily operations.

## Timeline
On Saturday 27th August 1000 hours (West Africa Time), Mr James reported that the master server was lagging in speed, which was the first indication of a problem. Our engineers disconnected the master server web-01 to investigate the issue and redirected all requests to the client server web-02. It took our team a total of 36 hours to solve the problem, with all services restored by Sunday 27th August 2200 hours (West Africa Time).

## Cause and resolution
The root cause of the problem was a memory outage in the master server web-01 due to the overwhelming number of requests it was receiving. During a previous test, the client server web-02 had been disconnected temporarily for testing purposes and was not reconnected to the load balancer afterward. This meant that all requests were directed to the master server, causing it to fail.

To resolve the issue, our engineers temporarily disconnected the master server to perform a memory clean-up. They then reconnected it to the load balancer, and configured a round-robin algorithm to ensure both the master and client servers could handle an equal amount of requests.

## Prevention against such problem in future
To prevent such problems from occurring in the future, we recommend the following measures:

Choose the best load-balancing algorithm for your programs. A round-robin algorithm can be very effective in distributing requests evenly between servers.
Always keep an eye on your servers to ensure they are running correctly. Regular maintenance and monitoring can help to detect issues early and prevent them from becoming more severe.
Have extra backup servers to prevent your program from completely going offline during an issue. This can help ensure that your users have access to your platform even if one or more servers fail.
