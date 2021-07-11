# hands-on-007

## A Simple EC2 Auto Scaling + Load Balancing


## Goal
This hands-on is a continuation of [hands-on-006](../hands-on-006) with a Load Balancer added.

## Architecture Diagram
![hands-on-007-arch-01](images/hands-on-007-arch-01.png)

## Overview

### Step 1 - Create the Application Load Balancer

Follow [step 5 of hands-on-005](../hands-on-005), but do not add any targets to the load balancer target group.  

### Step 2 - Edit the Auto Scaling Group

Edit the auto scaling group adding the load balancer target group created in the previous step.
![hands-on-007-scrn-01](images/hands-on-007-scrn-01.png)
![hands-on-007-scrn-02](images/hands-on-007-scrn-02.png)

## Test and Validation
Copy the DNS name associated with the load balancer and, using a browser, try to access it. You should be able to see the response associated with the only EC2 instance that is running and automatically launched by the auto scaling service. Now connect to this instance through SSH and run the following commands to artificially increase CPU utilization.

```
stress -c 200
```
You can then begin monitoring the instance's CPU utilization increase and verify than when it reaches 75% or above a new EC2 instance will automatically be launched by the auto scaling service. When that happens, verify that the auto scaling service will automatically launch a second EC2 instance. Now using the DNS associated with the load balancer, verify whether you are able to see responses from both instances as you refresh the page. This test proves that the application load balancer is working properly by redirecting the request evenly to the two instances.
