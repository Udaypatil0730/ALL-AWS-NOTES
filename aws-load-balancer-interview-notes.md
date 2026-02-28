AWS Load Balancer & Target Group – Interview Revision Notes
1. Load Balancer – Definition

Definition:
Load Balancer distributes incoming traffic across multiple EC2 instances to ensure high availability, fault tolerance, and performance.

Keywords:
Traffic distribution
High availability
Fault tolerance
No single point of failure

Ready-to-speak answer:
Load Balancer distributes incoming client requests across multiple EC2 instances in a target group to ensure high availability and prevent overload on a single instance.

2. Load Balancer Traffic Flow (MEMORIZE FLOW)

Client → Load Balancer → Listener → Target Group → EC2 instance → Response to client

Keywords:
Listener = receives request
Target Group = holds instances
EC2 = serves request

3. Target Group – Definition

Definition:
Target Group is a logical group of backend instances that receive traffic from Load Balancer.

Keywords:
Bridge between Load Balancer and EC2
Contains registered instances
Performs health checks

Ready-to-speak answer:
Target Group is a logical group of EC2 instances where Load Balancer forwards traffic and performs health checks to ensure only healthy instances receive traffic.

4. Target Group Health Check

Purpose:
Ensures application is healthy before sending traffic.

Health check example:

Protocol: HTTP
Port: 80
Path: /health

Keywords:
Health check verifies application
Unhealthy instance = no traffic

5. Listener – Definition

Definition:
Listener checks for incoming requests on a specific protocol and port and forwards traffic to Target Group.

Example:

HTTP : 80
HTTPS : 443

Keywords:
Listener listens on port
Listener forwards traffic

Ready-to-speak answer:
Listener listens for incoming traffic on a specific protocol and port and forwards it to the configured target group.

6. Listener Rule – Definition

Definition:
Listener Rule defines routing based on conditions like path or hostname.

Example:

/api → target-group-api
/web → target-group-web

Keywords:
Path-based routing
Host-based routing
Priority-based routing

7. Types of Load Balancer
A. Application Load Balancer (ALB)

Layer: 7

Protocol: HTTP, HTTPS

Features:

Path-based routing

Host-based routing

Keywords:
Most used
Layer 7 routing

B. Network Load Balancer (NLB)

Layer: 4

Protocol: TCP, UDP

Features:

Ultra low latency

High performance

Keywords:
Layer 4
High performance

C. Classic Load Balancer (CLB)

Status: Legacy

Keywords:
Old load balancer
Not recommended

8. Load Balancer and Auto Scaling Integration

Flow:

Auto Scaling launches instance → registers to Target Group → Load Balancer sends traffic

Keywords:
Automatic registration
Automatic deregistration

9. Common Troubleshooting Scenarios
Scenario 1: Instance not receiving traffic

Check:

Target Group registration

Health check status

Security group rules

Application running

Scenario 2: Target Group health check failing

Check:

Application running

Health check path

Port listening

Security group

Scenario 3: Load Balancer DNS not accessible

Check:

Load Balancer SG inbound rule

Internet-facing configuration

Listener configuration

Route table and IGW

Scenario 4: Load Balancer returns 502 / 503

Meaning:

502 → Load Balancer cannot connect to instance
503 → No healthy instances

Check:

Application running

Target group health

Port listening

Security group

10. Load Balancer vs Auto Scaling (Important)

Load Balancer → distributes traffic
Auto Scaling → creates/removes instances

Keywords:
Load Balancer = traffic manager
Auto Scaling = capacity manager

11. Real-world Production Architecture (MEMORIZE)

Client
↓
Load Balancer
↓
Listener
↓
Target Group
↓
Auto Scaling Group
↓
EC2 instances

12. Final Interview Summary (MOST IMPORTANT)

Load Balancer distributes incoming traffic to healthy EC2 instances in a target group using listeners and routing rules, while performing health checks to ensure high availability and reliability.