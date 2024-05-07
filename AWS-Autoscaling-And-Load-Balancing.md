# Configuring Auto Scaling with an Application Load Balancer (ALB) using a Launch Template

## Purpose

In this mini project, you will learn how to configure Auto Scaling in AWS with an Application Load Balancer (ALB), using a Launch Template. The project aims to demonstrate the automatic scaling of EC2 instances based on demand while leveraging the benefits of a Launch Template.

## Objectives

1. Create Launch Template:
Learn how to create a Launch Template with the required specifications.
2. Set Up Auto Scaling Group:
Configure an Auto Scaling group to manage the desired number of EC2 instances using Launch Template
3. Configure Scaling Policies:
Set up scaling policies to adjust the number of instances based on demand.
4. Attach ALB to Auto Scaling Group:
Connect the Auto Scaling Group to an existing ALB.
5. Test Auto Scaling:
Generate traffic to trigger scaling policies.

## Project Tasks

### 1. Create Launch Template

To create a Launch Template in AWS, follow these steps:

Log in to the AWS Management Console.
Navigate to the EC2 service.
Click on “Launch Templates” under the Instances section.
Click on “Create launch template” and provide the necessary specifications such as AMI ID, instance type, key pair, security groups, etc.
Save the launch template.

### 2. Set Up Auto Scaling Group

To configure an Auto Scaling group using the Launch Template:

Go to the EC2 Dashboard and select “Auto Scaling Groups.”
Click on “Create an Auto Scaling group” and choose the launch template you created.
Define the desired number of instances, network settings, scaling options, etc.
Complete the setup by following the on-screen instructions.

### 3. Configure Scaling Policies

To set up scaling policies for adjusting the number of instances based on demand:

In the Auto Scaling group settings, navigate to “Scaling Policies.”
Click on “Add policy” and define conditions such as scaling based on CPU utilization or other metrics.
Specify whether to scale out (add instances) or scale in (remove instances) based on thresholds.
Save the scaling policy.

### 4. Attach ALB to Auto Scaling Group

To connect the Auto Scaling Group to an existing ALB:

Go to the EC2 Dashboard and select “Target Groups” under Load Balancing.
Choose your ALB and click on “Edit attributes.”
Add your Auto Scaling Group as a target for the ALB.

### 5. Test Auto Scaling

To test auto scaling by generating traffic:

Install stress tool using:
 sudo amazon-linux-extras install epel -y
 sudo yum install stress -y
Generate load using stress tool:
 stress -c 4
Monitor and verify that the Auto Scaling group adjusts the number of instances in response to changes in demand.

## The Significance of the Auto Scaling

Auto scaling is a critical feature in cloud computing that allows resources to automatically adjust based on the current workload. This capability is essential for optimizing resource utilization and maintaining application performance during varying workloads for several reasons:

1. Cost Efficiency: Auto scaling helps organizations save costs by automatically scaling resources up or down based on demand. This ensures that resources are only used when needed, preventing over-provisioning and unnecessary expenses.

2. Improved Performance: By automatically adjusting resources to match the current workload, auto scaling helps maintain consistent application performance even during peak usage periods. This ensures that users have a seamless experience without any performance degradation.

3. Scalability: Auto scaling enables applications to easily handle sudden spikes in traffic or workload without manual intervention. This scalability ensures that applications can quickly adapt to changing demands without impacting performance.

4. Resource Optimization: Auto scaling helps optimize resource utilization by dynamically allocating resources based on demand. This ensures that resources are efficiently utilized, leading to better overall performance and cost savings.

5. Flexibility: Auto scaling provides flexibility for organizations to easily adjust resources based on changing requirements. This agility allows organizations to quickly respond to market changes and scale their applications as needed.

Overall, auto scaling is a crucial tool for optimizing resource utilization and maintaining application performance during varying workloads in a cost-effective and efficient manner.

**Setting up scaling policies in AWS Auto Scaling involves defining rules that determine when and how the Auto Scaling group should add or remove instances based on specific metrics. Here's a more detailed guide on how to configure scaling policies within an Auto Scaling group:**

1. **Log in to AWS Console and Navigate to Auto Scaling Groups:**
   - Go to the EC2 dashboard.
   - In the left-hand menu, under "Auto Scaling," select "Auto Scaling Groups."

2. **Select Your Auto Scaling Group:**
   - Choose the Auto Scaling group to which you want to add scaling policies by clicking on its name.

3. **Navigate to Scaling Policies Section:**
   - Within your Auto Scaling group's details, click on the "Scaling Policies" tab.

4. **Add Scaling Policy:**
   - Click on the "Add policy" button to create a new scaling policy.

5. **Choose Scaling Metric:**
   - In the "Metric Type" dropdown, select the metric you want to use for scaling. Common metrics include:
     - **Target Tracking Scaling:** Maintain a target value for a specific metric (e.g., CPU utilization, request count per target) and Auto Scaling adjusts the number of instances to keep the metric at the target value.
     - **Simple Scaling:** Define scaling actions based on a single CloudWatch alarm threshold (e.g., scale out if CPU utilization > 70%, scale in if CPU utilization < 30%).
     - **Step Scaling:** Define scaling adjustments based on a set of scaling steps. Each step defines a lower and upper threshold and the number of instances to add or remove when the threshold is breached.

6. **Configure Scaling Policy:**
   - Depending on the chosen metric type, configure the policy settings:
     - For **Target Tracking Scaling:**
       - Set the target value for the metric.
       - Specify the scaling behavior (e.g., scale in and scale out cooldown periods).
     - For **Simple Scaling:**
       - Choose the CloudWatch alarm for the metric and define the scaling actions for "Increase Group Size" and "Decrease Group Size."
     - For **Step Scaling:**
       - Define the scaling adjustments for each step based on the metric thresholds.

7. **Review and Create Policy:**
   - Review the configured scaling policy to ensure it aligns with your requirements.
   - Click on "Create" or "Save" to create the scaling policy.

8. **Repeat for Additional Policies (Optional):**
   - If you need multiple scaling policies (e.g., one for CPU utilization, another for request count), repeat the above steps to add more policies.

9. **Adjust Cooldown Periods (Optional):**
   - Consider adjusting cooldown periods for scale in and scale out actions to prevent rapid scaling events that might lead to instability or unnecessary costs.

10. **Monitor and Test:**
    - Once your scaling policies are set up, monitor your Auto Scaling group's behavior in the AWS Console.
    - Test your scaling policies by generating load or triggering events that exceed the defined thresholds to ensure that instances are scaled in or out as expected.

By following these steps, you can effectively set up scaling policies within your Auto Scaling group to automate instance scaling based on predefined criteria and metrics.
