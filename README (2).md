<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-iam)

**Author:** Kevin Kier Lo  
**Email:** kevinkierlo29@gmail.com

---

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to create EC2 instances, define custom IAM policies, organize IAM users into user groups, and set up an AWS account alias. I’m doing this project to learn the fundamentals of AWS security and access management, and how to safely operate compute resources without using the root account.

### Tools and concepts

Services I used were Amazon EC2 and AWS IAM. Key concepts I learnt include IAM users, user groups, policies, account aliases, permissions, resource tags, and the IAM Policy Simulator.

### Project reflection

This project took me approximately 1 hour. The most challenging part was setting up and testing the IAM policies correctly. It was most rewarding to successfully control access to the development and production EC2 instances.

---

## Tags

### What I did in this step

In this step, I will launch two Amazon EC2 instances to increase NextWork’s computing capacity for the holiday traffic surge. I’m doing this because additional EC2 instances provide the extra compute power needed to handle more website users without slowing down or crashing.

### Understanding tags

Tags are labels or key-value pairs attached to AWS resources to help identify, organize, and manage them. They are useful for tracking resources, separating environments, and managing costs.

### My tag configuration

The tag I’ve used on my EC2 instances is called Env. The value I’ve assigned for my instances are production and development.

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an IAM policy that gives the intern permission to access the development EC2 instance because they need to work on and test the development environment without having access to the production instance.

### Understanding IAM policies

IAM Policies are documents that define what actions a user, group, or role is allowed or denied to perform on AWS resources.

### The policy I set up

For this project, I’ve set up a policy using JSON.

### Policy effect

I’ve created a policy that allows the intern to access EC2 resources in the development environment, while preventing them from accessing production resources.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means Effect defines whether an action is allowed or denied, Action specifies what actions can be performed, and Resource identifies which AWS resources the policy applies to.

---

## My JSON Policy

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will create an Account Alias for the AWS account because it will make it easier for the intern to find and access the AWS account login page.

### Understanding account aliases

An account alias is a unique name that makes it easier to identify and access your AWS account instead of using the account ID.

### Setting up my account alias

Creating an account alias took me 3 seconds. Now, my new AWS console sign-in URL is https://nextwork-alias-kevinlo.signin.aws.amazon.com/console

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will create an IAM group for NextWork interns and an IAM user for the new intern because the group will let me manage their permissions in one place, while the user will give the intern their own secure way to log in.

### Understanding user groups

IAM user groups are collections of IAM users that share the same permissions and policies, making it easier to manage access for multiple users at once.

### Attaching policies to user groups

I attached the policy I created to this user group, which means all users added to the group will receive the permissions defined in the policy, allowing them to access the development EC2 instance.

### Understanding IAM users

IAM users are individual identities created in AWS for people or applications that need access to AWS resources.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to share the sign-in details directly with the user. The second way is to have AWS send the user an email with instructions to sign in and set up their password.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that I could access the AWS console, but I had limited access compared to the main account. This was because the IAM user only had the permissions provided by the policy attached to the interns' group.

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log into AWS using the intern's IAM user and test access to both the development and production EC2 instances because I need to verify that the intern can access the development environment but cannot access the production environment.

### Testing policy actions

I tested my JSON IAM policy by trying to stop both the development and production EC2 instances.

### Stopping the production instance

When I tried to stop the production instance, the action failed because I was not authorized to stop instances with the production tag. This was because my IAM user only had permission to access resources in the development environment.

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, the instance was successfully stopped. This was because my IAM policy allows me to perform EC2 actions on resources tagged with Env: development.

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to use the IAM Policy Simulator to test the intern's permissions. I'm doing this because it allows me to verify access to the development and production environments without actually affecting or stopping my EC2 instances.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that lets me test and validate IAM permissions without affecting actual AWS resources. It's useful for checking whether users have the correct access before applying changes in a real environment.

### How I used the simulator

I set up a simulation for the ec2:StopInstances action on the development instance. The results were allowed, confirming that the policy gives the intern permission to stop the development instance. I had to adjust the resource selection to use the development instance/resource tags.

![Image](http://nextwork.ai/joyful_lavender_trusty_freshwater_mussel/uploads/aws-security-iam_069d8a621)

---

---
