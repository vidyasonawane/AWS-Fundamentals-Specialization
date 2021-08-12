
1. You should consider four main aspects when deciding which AWS Region to host your applications and workloads: latency, price, service availability, and compliance. Focusing on these factors will enable you to make the right decision when choosing an AWS Region. You can find this content in the AWS Global Infrastructure video. 

2. In AWS, every action you make is an API call that is authenticated and authorized. You can make API calls to services and resources through the AWS Management Console, the AWS Command Line Interface (CLI), or the AWS Software Development Kits (SDKs). This content is covered in Interacting with AWS.  

3. The AWS Global Infrastructure is nested for high availability and redundancy. AWS Regions are clusters of Availability Zones that are connected through highly availably and redundant high-speed links and Availability Zones are clusters of data centers that are also connected through highly available and redundant high-speed links. This content is covered in the AWS Global Infrastructure video.

4. There are six benefits of cloud computing. The correct answer for this question is “go global in minutes.” Going global in minutes means you can easily deploy your applications in multiple Regions around the world with just a few clicks.

5. With the cloud, you no longer have to manage and maintain your own hardware in your own data centers. Companies like AWS own and maintain these data centers and provide virtualized data center technologies and services to users over the internet. 

6. You use an access key (an access key ID and secret access key) to make programmatic requests to AWS. However, do not use your AWS account root user access key. The access key for your AWS account root user gives full access to all your resources for all AWS services, including your billing information. You cannot reduce the permissions associated with your AWS account root user access key. Therefore, protect your root user access key like you would your credit card numbers or any other sensitive secret. You should disable to delete any access keys associated with the root user, and you should also enable MFA for the root user.

7. Instead of creating an IAM User for each employee that needs access to the AWS account, you should use IAM Roles to federate users. Read more here: https://aws.amazon.com/identity/federation/

8. A policy is an object in AWS that, when associated with an identity or resource, defines their permissions. AWS evaluates these policies when an IAM principal (user or role) makes a request. Permissions in the policies determine whether the request is allowed or denied. Most policies are stored in AWS as JSON documents that are attached to an IAM identity (user, group of users, or role). The information in a policy statement is contained within a series of elements:

    - Version – Specify the version of the policy language that you want to use. As a best practice, use the latest 2012-10-17 version.
    - Statement – Use this main policy element as a container for the following elements. You can include more than one statement in a policy.
    - Sid (Optional) – Include an optional statement ID to differentiate between your statements.
    - Effect – Use Allow or Deny to indicate whether the policy allows or denies access.
    - Principal (Required in only some circumstances) – If you create a resource-based policy, you must indicate the account, user, role, or federated user to which you would like to allow or deny access. If you are creating an IAM permissions policy to attach to a user or role, you cannot include this element. The principal is implied as that user or role.
    - Action – Include a list of actions that the policy allows or denies.
    - Resource (Required in only some circumstances) – If you create an IAM permissions policy, you must specify a list of resources to which the actions apply. If you create a resource-based policy, this element is optional. If you do not include this element, then the resource to which the action applies is the resource to which the policy is attached.
    - Condition (Optional) – Specify the circumstances under which the policy grants permission.

9. The AWS account root user gives full access to all your resources for all AWS services, including your billing information. **You cannot reduce the permissions associated with your AWS account root user** access key.

10. Multi-factor Authentication is an authentication method that requires the user to provide two or more verification factors to gain access to an AWS account.