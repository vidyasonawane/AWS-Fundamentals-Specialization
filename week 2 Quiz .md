**Question 1** : Which of the following pieces of information do you need to create a Virtual Private Cloud (VPC)?
- The Availability Zone it will reside in.
- **The AWS Region it will reside in.**
- The group of subnets it will reside in.
- The subnet it will reside in.

- Ans: When you create a VPC, you have to specify the AWS region it will reside in, the IP range for the VPC, as well as the name of the VPC. This content is covered in the video “Introduction to Amazon VPC” 

**Question 2**: Which of the following can a route table be attached to?
- AWS Accounts
- Availability Zone
- **Subnets**
- Regions

- ans: Route Tables can be attached to VPCs and subnets. Therefore, answer “c” is correct. You can find this information in the video “Amazon VPC Routing” 

**Question 3**: What must you do to allow resources in a public subnet to communicate with the internet?
- Create a route to a private subnet.
- **Attach an internet gateway to your VPC.**
- **Create a route in a route table to the internet gateway.**

- ans : To allow your resources to communicate with the internet, you’ll need to attach an internet gateway to your VPC, and create a route in a route table to the internet gateway and attach it to your subnet with your internet-facing resources. You’ll also need to make sure your internet-facing resources have a public IP address. This content can be found in “Introduction to Amazon VPC” and “Amazon VPC Routing”. 

**Question 4**: True or false: A network ACL filters traffic at the EC2 instance level.
- True
- **False**

- ans: The answer is false. A network ACL secures subnets, while a security group is responsible for securing EC2 instances. This content is covered in the video “Secure your network with Amazon VPC Security”.

**Question 5**: Which of the following is true for the default settings of a security group?
- Allows all inbound traffic and blocks all outbound traffic.
- **Blocks all inbound traffic and allows all outbound traffic.**
- Allows all inbound and outbound traffic.
- Blocks all inbound and outbound traffic.

- ans: The default configuration of a security group blocks all inbound traffic and allows all outbound traffic. This content is covered in the video “Secure your network with Amazon VPC Security”.

**Question 6**: What does an Amazon EC2 instance type indicate?
- **Instance family and instance size**
- Instance placement and instance size
- Instance tenancy and instance billing
- Instance AMI and networking speed

- ans: Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload. You can find this information in the Introduction to Amazon EC2 video.

**Question 7**: True or false: EC2 instances reside at the Availability Zone level, so it’s best practice to architect for high availability.
- **True**
- False

- ans : When you launch an Amazon EC2 instance, you must choose the subnet to place the instance into. Subnets reside in one singular AZ and cannot span AZs, therefore EC2 instances also reside in one Availability Zone. You should architecture for high availability in case one AZ is unreachable for any reason or is experiencing outages. To do so, you should deploy AWS resources, like Amazon EC2, should be deployed redundantly across at least two AZs.  You can find this information in the Introduction to Amazon EC2 video and corresponding notes section.

**Question 8**: What is the difference between AWS Fargate and Amazon ECS on EC2?
- **With AWS Fargate, AWS manages and provisions the underlying infrastructure for hosting your containers.**
- With AWS Fargate, you have to manage cluster capacity and scaling.
- With Amazon ECS on EC2, AWS manages and provisions the underlying EC2 instance for your containers.
- With Amazon ECS on EC2, you only have to upload your source code and ECS takes care of the rest.

- ans: AWS Fargate is a serverless compute platform for either Amazon ECS or Amazon EKS. When you use Fargate, the compute infrastructure needed to run containers is managed by AWS whereas with Amazon ECS on EC2 for the compute platform you are responsible for managing the underlying EC2 cluster hosting your containers. You can find this information in the Containers on AWS video and corresponding notes section.

**Question 9**: Which of the following is true about serverless?
- You must manage availability and fault tolerance.
- You must provision and manage servers.
- You must manually scale serverless resources.
- **You never pay for idle resources.**

-ans: With serverless on AWS you do not have to pay for idling resources, instead you only pay for what you use and each serverless service will charge differently based on usage. You can find this in the What is serverless video and corresponding notes section.

**Question 10**: True or false: AWS Lambda is always the best solution when running applications on AWS.
- True
- **False**

- ans : AWS Lambda is a great solution for many use cases, but it does not fit all use cases. For long running processes, Lambda is not the best choice since it has a 15 minute runtime limit. Read about use cases for AWS Lambda here: https://docs.aws.amazon.com/lambda/latest/dg/applications-usecases.html You can find information this in the Choose the Right Compute Service video.

**Question 11**: True or false: Amazon EC2 is best suited for applications where you need more convenience and less control.
- True
- **False**

- ans : Amazon EC2 provides you with a great deal of control over the environment your application runs in, serverless services like AWS Lambda exist to provide convenience whereas services like Amazon EC2 provide control. You can find this in the What is Serverless video.