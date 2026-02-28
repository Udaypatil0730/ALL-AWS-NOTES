AWS Auto Scaling – Interview Revision Notes (DevOps / Cloud Engineer)
1. Auto Scaling – Definition

Definition:
Auto Scaling automatically adds or removes EC2 instances based on load to maintain performance and optimize cost.

Keywords:
High availability Fault tolerance Elasticity Cost optimization

Ready-to-speak answer:
Auto Scaling ensures application availability by automatically launching or terminating EC2 instances based on defined scaling policies and health checks.

2. Core Components Flow (Architecture Chain)

Flow (MEMORIZE THIS ORDER):

EC2 → AMI → Launch Template → Auto Scaling Group → Target Group → Load Balancer → CloudWatch → Scaling Policy

Keywords:
Launch Template = blueprint
ASG = controller
CloudWatch = monitoring
Scaling Policy = decision maker

3. Launch Template

Definition:
Launch Template is a blueprint used by Auto Scaling Group to launch EC2 instances.

Contains:

AMI ID

Instance type

Security group

IAM role

Key pair

User data

Important point:
Launch Template supports versioning.

Interview answer:
Launch Template is used by Auto Scaling Group as a blueprint to launch EC2 instances with predefined configuration.

4. Desired vs Min vs Max Capacity

Desired Capacity:
Number of instances Auto Scaling maintains.

Minimum Capacity:
Lower limit (never goes below this)

Maximum Capacity:
Upper limit (never goes above this)

Example:

Min = 2
Desired = 3
Max = 6

Keywords:
Min ≤ Desired ≤ Max

Interview answer:
Desired capacity is the number of instances Auto Scaling maintains, minimum is the lower limit, and maximum is the upper limit for scaling.

5. Scaling Policies (VERY IMPORTANT)
A. Target Tracking Scaling (Most used)

Definition:
Maintains a target metric value automatically.

Example:
Target CPU = 70%

Keywords:
Automatic scaling
AWS decides scaling

Interview answer:
Target tracking automatically adjusts the number of instances to maintain a target metric value like CPU utilization.

B. Step Scaling

Definition:
Scaling based on predefined steps.

Example:

CPU 70–80% → add 1 instance
CPU 80–90% → add 2 instances

Keywords:
Manual steps
CloudWatch alarm based

C. Simple Scaling (Legacy)

Definition:
Scaling based on single CloudWatch alarm.

6. Scale-Out vs Scale-In

Scale-Out:
Add instances when load increases

Scale-In:
Remove instances when load decreases

Keywords:
Scale-out = add instances
Scale-in = remove instances

Interview answer:
Scale-out launches new instances during high load, and scale-in terminates instances during low load.

7. Health Checks in Auto Scaling
1. EC2 Health Check

Checks:

System status check

Instance status check

2. Load Balancer Health Check

Checks:

Application response

Keywords:
EC2 check = OS + infrastructure
LB check = application health

8. What happens when instance becomes unhealthy

Flow:

Unhealthy detected → Deregister from Target Group → Terminate instance → Launch new instance → Health check → Register → Serve traffic

Keywords:
Replace, not repair

Interview answer:
Auto Scaling terminates unhealthy instances and launches new instances to maintain desired capacity.

9. Instance Refresh

Definition:
Replaces old instances with new instances using latest Launch Template.

Purpose:

Update AMI

Update configuration

Security patching

Keywords:
Zero downtime
Rolling replacement

Interview answer:
Instance Refresh replaces existing instances with new instances using updated launch template without downtime.

10. Cooldown Period

Definition:
Time Auto Scaling waits after scaling activity before scaling again.

Default:
300 seconds

Keywords:
Prevent over scaling

11. Health Check Grace Period

Definition:
Time Auto Scaling waits before checking health of new instance.

Purpose:
Allow instance startup time.

Keywords:
Prevent false unhealthy detection

12. Lifecycle Hook

Definition:
Allows pausing instance launch or termination to perform custom actions.

States:

Pending:Wait
Terminating:Wait

Use cases:

Install application

Configure monitoring

Backup logs

Interview answer:
Lifecycle hook pauses instance launch or termination to perform custom actions before instance serves traffic or terminates.

13. Complete Auto Scaling Flow (MOST IMPORTANT)

Full flow:

EC2 sends CPU metrics to CloudWatch

CloudWatch triggers scaling policy

Auto Scaling launches instance using Launch Template

Instance passes health check

Instance registers with Target Group

Load Balancer sends traffic

Load distributes → CPU reduces

14. Most Important Interview One-Line Summary

Auto Scaling monitors EC2 metrics using CloudWatch and automatically launches or terminates instances using launch templates based on scaling policies to maintain performance and availability.

15. Most Common Interview Questions List (Revision Checklist)

You must revise these:

What is Auto Scaling?

What is Launch Template?

Desired vs Min vs Max capacity

Target tracking vs Step scaling

Scale-out vs Scale-in

Health checks

Instance refresh

Cooldown period

Lifecycle hook

What happens when instance becomes unhealthy?