Module 19: Cloud Computing
Scenario
Cloud computing is an emerging technology that delivers computing services such as online business applications, online data storage, and webmail over the Internet. Cloud implementation enables a distributed workforce, reduces organization expenses, provides data security, etc. As enterprises are increasingly adopting cloud services, cloud systems have emerged as targets for attackers to gain unauthorized access to the valuable data stored in them. Therefore, it is essential to regularly perform pen testing on cloud systems to monitor their security posture.
Security administrators claim that cloud systems are more vulnerable to DoS assaults, because they involves numerous individuals or clients, making DoS assaults potentially very harmful. Because of the high workload on a flooded service, these systems attempt to provide additional computational power (more virtual machines, more service instances) to cope with the workload, and they will eventually fail.
Although cloud systems try to thwart attackers by providing additional computational power, they inadvertently aid attackers by allowing the most significant possible damage to the availability of a service—a process that starts from a single flooding-attack entry point. Thus, attackers need not flood all servers that provide a particular service but merely flood a single, cloud-based address to a service that is unavailable. Thus, adequate security is vital in this context, because cloud-computing services are based on sharing.
As an ethical hacker and penetration tester, you must have sound knowledge of hacking cloud platforms using various tools and techniques. The labs in this module will provide you with real-time experience in exploiting the underlying vulnerabilities in a target cloud platform using various hacking methods and tools. However, hacking the cloud platform may be illegal depending on the organization’s policies and any laws that are in effect. As an ethical or pen tester, you should always acquire proper authorization before performing system hacking.
Objective
The objective of the lab is to perform cloud platform hacking and other tasks that include, but are not limited to:
• Performing S3 bucket enumeration
• Exploiting misconfigured S3 buckets
• Escalating privileges of a target IAM user account by exploiting misconfigurations in a user policy
Overview of Cloud Computing
Cloud computing refers to on-demand delivery of IT capabilities, in which IT infrastructure and applications are provided to subscribers as metered services over a network. Cloud services are classified into three categories, namely infrastructure-as-a-service (IaaS), platform-as-a-service (PaaS), and software-as-a-service (SaaS), which offer different techniques for developing cloud.
Lab Tasks
Ethical hackers or pen testers use numerous tools and techniques to hack the target cloud platform. Recommended labs that will assist you in learning various cloud platform hacking techniques include:
1. Perform S3 bucket enumeration using various S3 bucket enumeration tools
• Enumerate S3 buckets using lazys3
• Enumerate S3 buckets using S3Scanner
2. Exploit S3 buckets
• Exploit open S3 buckets using AWS CLI
3. Perform privilege escalation to gain higher privileges
• Escalate IAM user privileges by exploiting misconfigured user policy
PreviousNext

From <https://labclient.labondemand.com/Instructions/63c28e91-a756-4f02-8772-09792bbc3769> 

Lab 1: Perform S3 Bucket Enumeration using Various S3 Bucket Enumeration Tools
Lab Scenario
As an ethical hacker, you must try to obtain as much information as possible about the target cloud environment using various enumeration tools. This lab will demonstrate various S3 bucket enumeration tools that can help you in extracting the list of publicly available S3 buckets.
Lab Objectives
• Enumerate S3 buckets using lazys3
• Enumerate S3 buckets using S3Scanner
Overview of Enumeration Tools
Enumeration tools are used to collect detailed information about target systems to exploit them. Information collected by S3 enumeration tools consists of a list of misconfigured S3 buckets that are available publicly. Attackers can exploit these buckets to gain unauthorized access to them. Moreover, they can modify, delete, and exfiltrate the bucket content.
Task 1: Enumerate S3 Buckets using lazys3
lazys3 is a Ruby script tool that is used to brute-force AWS S3 buckets using different permutations. This tool obtains the publicly accessible S3 buckets and also allows you to search the S3 buckets of a specific company by entering the company name.
	1. Click Parrot Security2 to switch to the Parrot Security machine.
	
	2. In the login page, the attacker username will be selected by default. Enter password as toor in the Password field and press Enter to log in to the machine.
	
	3. Click the MATE Terminal icon at the top of the Desktop window to open a Terminal window.
	
	4. A Parrot Terminal window appears. In the terminal window, type sudo su and press Enter to run the programs as a root user.
If a Question pop-up window appears asking for you to update the machine, click No to close the window.
	5. In the [sudo] password for attacker field, type toor as a password and press Enter.
The password that you type will not be visible.
	
	6. In the terminal window, type cd lazys3-master/ and press Enter to navigate to the cloned repository.
We have already downloaded lazys3 tool in the Lab setup.
	
	7. In the lazys3 folder, type ls and press Enter to list the folder content.
	8. The folder content is displayed; here, we will run the lazys3.rb script to find the public S3 buckets.
	
	9. Now, type ruby lazys3.rb and press Enter.
	10. A list of public S3 buckets is displayed, as shown in the screenshot.
	
	11. Press Ctrl+Z to stop the script.
	
	12. You can search the S3 buckets of specific company. To do so, type ruby lazys3.rb [Company] and press Enter.
Here, the target company name is HackerOne; you can enter the company name of your choice.
	13. The result appears, showing the obtained list of S3 buckets of the specified company.
It will take some time to obtain a complete list of the available S3 buckets.
	
	14. Press Ctrl+Z to stop running the script.
	15. This concludes the demonstration of enumerating public S3 buckets.
	16. Close all open windows and document all acquired information.

Task 2: Enumerate S3 Buckets using S3Scanner
S3Scanner is a tool that finds the open S3 buckets and dumps their contents. It takes a list of bucket names to check as its input. The S3 buckets that are found are output to a file. The tool also dumps or lists the contents of “open” buckets locally.
Here, we will use the S3Scanner tool to enumerate open S3 buckets.
	1. Click the MATE Terminal icon in the menu to launch the terminal.
	
	2. A Parrot Terminal window appears. In the terminal window, type sudo su and press Enter to run the programs as a root user.
	3. In the [sudo] password for attacker field, type toor as a password and press Enter.
The password that you type will not be visible.
	
	4. Type cd S3Scanner/ and press Enter to navigate to the cloned repository.
By default, the tool is cloned to the root directory.
	5. In the S3Scanner folder, type pip3 install -r requirements.txt and press Enter to install the required dependencies.
	
	6. After the successful installation of the dependencies, in the terminal window, type python3 ./s3scanner.py sites.txt and press Enter to run the tool.
Here, sites.txt is a text file containing the target website URL that is scanned for open S3 buckets. You can edit the sites.txt file to enter the target website URL of your choice.
	7. The result appears, displaying a list of public S3 buckets, as shown in the screenshot.
You might encounter the following error: “AWS credentials not configured.” Ignore the error, as we will install and configure the AWS CLI in the next lab.
	
	8. This concludes the demonstration of enumerating S3 buckets using the S3Scanner tool.
	9. You can also use other S3 bucket enumeration tools such as S3Inspector (https://github.com), s3-buckets-bruteforcer (https://github.com), Mass3 (https://github.com), Bucket Finder (https://digi.ninja), and s3recon (https://github.com) to perform S3 bucket enumeration for a target website or company.
	10. Close all open windows and document all acquired information.
Question 19.1.2.1
Use the S3Scanner tool to enumerate open S3 buckets. What is the size (in bytes) of a publicly accessible S3 bucket owned by flaws.cloud?
python3 ./s3scanner.py sites.txt

From <https://labclient.labondemand.com/Instructions/1093a13b-c983-4b93-8b24-88360f5d1d1e?showWhenStarting=1> 


PreviousNext

From <https://labclient.labondemand.com/Instructions/63c28e91-a756-4f02-8772-09792bbc3769> 



Lab 2: Exploit S3 Buckets
Lab Scenario
As a professional ethical hacker or pen tester, you must have sound knowledge of enumerating S3 buckets. Using various techniques, you can exploit misconfigurations in bucket implementation and breach the security mechanism to compromise data privacy. Leaving the S3 bucket session running enables you to modify files such as JavaScript or related code and inject malware into the bucket files. Furthermore, finding the bucket’s location and name will help you in testing its security and identifying vulnerabilities in the implementation.
Lab Objectives
• Exploit open S3 buckets using AWS CLI
Overview of S3 Buckets
S3 buckets are used by customers and end users to store text documents, PDFs, videos, images, etc. To store all these data, the user needs to create a bucket with a unique name.
Listed below are several techniques that can be adopted to identify AWS S3 Buckets:
• Inspecting HTML: Analyze the source code of HTML web pages in the background to find URLs to the target S3 buckets
• Brute-Forcing URL: Use Burp Suite to perform a brute-force attack on the target bucket’s URL to identify its correct URL
• Finding subdomains: Use tools such as Findsubdomains and Robtex to identify subdomains related to the target bucket
• Reverse IP Search: Use search engines such as Bing to perform reverse IP search to identify the domains of the target S3 buckets
• Advanced Google hacking: Use advanced Google search operators such as “inurl” to search for URLs related to the target S3 buckets
Task 1: Exploit Open S3 Buckets using AWS CLI
The AWS command line interface (CLI) is a unified tool for managing AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.
Caution: To complete the steps in this exercise, you will be required to sign up for third-party services that may incur fees. Make sure to follow proper guidelines to remove billable services from your account before leaving the lab. Deviating from our specific instructions may result in unwanted fees for services from third-party service providers. Check with your school, instructor, or employer for the availability of education accounts. If you provide your credit card information while signing up, you will be responsible for any fees related to the services you activate. We strongly advise you to not deviate from our explicit instructions while connected to the platforms unless you are fully aware of the services and their fees.
Note: Before starting this lab, you should create an AWS account using the following link: https://portal.aws.amazon.com/billing/signup#/start/email. After registration, perform the following tasks.
	1. Click Ubuntu to switch to the Ubuntu machine. In the login page, enter password as toor in the Password field and press Enter to log in to the machine.
	
	2. In the left pane, under Activities list, click the icon to open the Terminal window.
	
	3. Now, type sudo su and press Enter to run the programs as a root user. In the [sudo] password for attacker field, type toor as a password and press Enter.
The password that you type will not be visible.
	
	4. Now, type cd and press Enter to jump to the root directory.
	
	5. In the terminal window, type pip3 install awscli and press Enter to install AWS CLI.
	
	)
	6. Once the installation is completed, type aws --help and press Enter to check whether AWS CLI is properly installed.
Here, the awscli is already installed.
Ignore the errors (if you find any).
	
	7. Now, we need to configure AWS CLI. To configure AWS CLI in the terminal window, type aws configure and press Enter.
	
	8. It will ask for the following details:
	• AWS Access Key ID
	• AWS Secret Access Key
	• Default region name
	• Default output format
	9. To provide these details, you need to login to your AWS account.
	10. Cick Firefox icon from the top-left section of the Desktop.
	11. Login to your AWS account that you created at the beginning of this task. Click the Firefox browser icon in the menu, type https://console.aws.amazon.com in the address bar, and press Enter.
If you do not have an AWS account, create one with the Basic Free Plan, and then proceed with the tasks.
If the Root user email address option is not available click on Sign in using root user email button below Sign in button.
	12. The Amazon Web Services Sign-In page appears; type your email account in the Email address field and click Next.
	
	13. If the Security Check window appears, enter the captcha and click Submit.
If a browser notification appears at the top section of the window, click Don't Allow.
	14. Type your AWS account password in the Password field and click Sign in.
	
	15. Click the AWS account drop-down menu and click Security Credentials, as shown in the screenshot.
	
	16. Scrool down to get Access keys section.
	
	17. Click the Create access key button.
	
	18. A Create Access Key page appears, In Continue to create access key? make sure to check I understand creating a root access key is not a best practice, but I still want to create one and click on Create access key.
	
	19. A Access key created pop-up appears.
	
	20. Copy the Access Key ID displayed and switch to the Terminal window.
	
	21. In the terminal window, right-click your mouse; select Paste from the context menu to paste the copied Access Key ID and press Enter. It will prompt you to the AWS Secret Access Key. Switch to your AWS Account in the browser.
	
	22. In the Create Access Key pop-up, select the Secret Access Key displayed, and minimize the browser window. Switch to the Terminal window.
	23. In the terminal window, right-click your mouse, select Paste from the context menu to paste the copied Secret Access Key and press Enter. It will prompt you for the default region name.
	24. In the Default region name field, type eu-west-1 and press Enter.
	25. The Default output format prompt appears; leave it as default and press Enter.
	
	26. For demonstration purposes, we have created an open S3 bucket with the name certifiedhacker02 in the AWS service. We are going to use that bucket in this task.
The public S3 buckets can be found during the enumeration phase.
	27. Let us list the directories in the certifiedhacker02 bucket. In the terminal window, type aws s3 ls s3://[Bucket Name] (here, Bucket Name is certifiedhacker02) and press Enter.
The bucket name may be different in your lab environment depending on the bucket you are targeting.
	28. This will show you the list of directories in the certifiedhacker02 S3 bucket, as shown in the screenshot.
	
	29. Now, maximize the browser window, type certifiedhacker02.s3.amazonaws.com in the address bar, and press Enter.
	30. This will show you the complete list of directories and files available in this bucket.
	
	31. Minimize the browser window and switch to Terminal.
	32. Let us move some files to the ethicalhacking1 bucket. To do this, in the terminal window, type echo “You have been hacked” >> Hack.txt and press Enter.
	33. By issuing this command, you are creating a file named Hack.txt.
	
	34. Let us try to move the Hack.txt file to the certifiedhacker02 bucket. In the terminal window, type aws s3 mv Hack.txt s3://certifiedhacker02 and press Enter.
	35. You have successfully moved the Hack.txt file to the certifiedhacker02 bucket.
	
	36. To verify whether the file is moved, switch to the browser window and maximize it. Reload the page.
	37. You can observe that the Hack.txt file is moved to the certifiedhacker02 bucket, as shown in the screenshot.
	
	38. Minimize the browser window and switch to the Terminal window.
	39. Let us delete the Hack.txt file from the certifiedhacker02 bucket. In the terminal window, type aws s3 rm s3://certifiedhacker02/Hack.txt and press Enter.
	40. By issuing this command, you have successfully deleted the Hack.txt file from the certifiedhacker02 bucket.
	
	41. To verify whether the file is deleted, switch to the browser window and reload the page.
	42. The Hack.txt file is deleted from the certifiedhacker02 bucket.
	
	43. Thus, you can add or delete files from open S3 buckets.
	44. This concludes the demonstration of exploiting public S3 buckets.
	45. Close all open windows and document all the acquired information.
PreviousNext

From <https://labclient.labondemand.com/Instructions/63c28e91-a756-4f02-8772-09792bbc3769> 


Lab 3: Perform Privilege Escalation to Gain Higher Privileges
Lab Scenario
As a professional ethical hacker or pen tester, you must try to escalate privileges by employing a user account access key and secret access key obtained using various social engineering techniques. In privilege escalation, you attempt to gain complete access to the target IAM user’s account and, then try to attain higher-level privileges in the AWS environment.
In the cloud platform, owing to mistakes in the access allocation system such as coding errors and design flaws, a customer, a third party, or an employee can obtain higher access rights than those that they are authorized to use. This threat arises, because of authentication, authorization, and accountability (AAA) vulnerabilities, user provisioning and de-provisioning vulnerabilities, hypervisor vulnerabilities, unclear roles and responsibilities, misconfiguration, etc.
In this lab, we will exploit a misconfigured user permission policy to escalate privileges to the administrator level.
Lab Objectives
• Escalate IAM user privileges by exploiting misconfigured user policy
Overview of Privilege Escalation
Privileges are security roles assigned to users for using specific programs, features, OSes, functions, files, code, etc. to limit access depending on the type of user. Privilege escalation is required when you want to access system resources that you are not authorized to access. It takes place in two forms: vertical and horizontal.
• Horizontal Privilege Escalation: An unauthorized user tries to access the resources, functions, and other privileges of an authorized user who has similar access permissions
• Vertical Privilege Escalation: An unauthorized user tries to access the resources and functions of a user with higher privileges such as application or site administrators
Task 1: Escalate IAM User Privileges by Exploiting Misconfigured User Policy
A policy is an entity that, when attached to an identity or resource, defines its permissions. You can use the AWS Management Console, AWS CLI, or AWS API to create customer-managed policies in IAM. Customer-managed policies are standalone policies that you administer in your AWS account. You can then attach the policies to the identities (users, groups, and roles) in your AWS account. If the user policies are not configured properly, they can be exploited by attackers to gain full administrator access to the target user’s AWS account.
In this task, for demonstration purposes, we have created an IAM user account with permissions including iam:CreatePolicy, iam:AttachUserPolicy, iam:ListUserPolicies, sts:AssumeRole, and iam:ListRoles. These policies can be exploited by attackers to gain administrator-level privileges.
	1. In the Parrot Security machine, click the MATE Terminal icon in the menu to launch the terminal.
	
	2. A Parrot Terminal window appears. In the terminal window, type sudo su and press Enter to run the programs as a root user.
	3. In the [sudo] password for attacker field, type toor as a password and press Enter.
The password that you type will not be visible.
	4. Now, type cd and press Enter to jump to the root directory.
	
	5. In the terminal window, type aws configure and press Enter.
	6. Enter the details of the target IAM user’s access key in the AWS Access Key ID field and press Enter. Similarly, in the AWS Secret Access Key filed, enter the target IAM user’s secret access key and press Enter.
The AWS Access Key ID and AWS Secret Access Key of the target user’s account can be obtained using various social engineering techniques, as discussed in Module 09 Social Engineering.
	7. In the Default region name field, type us-east-2 and press Enter. In the Default output format field, type json and press Enter.
	
	8. After configuring the AWS CLI, we create a user policy and attach it to the target IAM user account to escalate the privileges.
	9. In the terminal window, type vim user-policy.json and press Enter.
This command will create a file named user-policy in the root directory.
	
	10. A command line text editor appears; press I and type the script given below:
{

TypeCopy
"Version":"2012-10-17",

"Statement": [
{

"Effect":"Allow",

"Action":"*",

"Resource":"*"

}

]
}
This is an AdministratorAccess policy that gives administrator access to the target IAM user.
Ignore the $ symbols in the script.
	11. After entering the script given in the previous step, press the Esc button. Then, type :wq! and press Enter to save the text document.
	
	12. Now, we will attach the created policy (user-policy) to the target IAM user’s account. To do so, type aws iam create-policy --policy-name user-policy --policy-document file://user-policy.json and press Enter.
	13. The created user policy is displayed, showing various details such as PolicyName, PolicyId, and Arn.
	
	14. In the terminal, type aws iam attach-user-policy --user-name [Target Username] --policy-arn arn:aws:iam::[Account ID]:policy/user-policy and press Enter.
	15. The above command will attach the policy (user-policy) to the target IAM user account (here, test).
	
	16. Now, type aws iam list-attached-user-policies --user-name [Target Username] and press Enter to view the attached policies of the target user (here, test).
	17. The result appears, displaying the attached policy name (user-policy), as shown in the screenshot.
	
	18. Now that you have successfully escalated the privileges of the target IAM user account, you can list all the IAM users in the AWS environment. To do so, type aws iam list-users and press Enter.
	19. The result appears, displaying the list of IAM users, as shown in the screenshot.
	
	20. Similarly, you can use various commands to obtain complete information about the AWS environment such as the list of S3 buckets, user policies, role policies, and group policies, as well as to create a new user.
	• List of S3 buckets: aws s3api list-buckets --query "Buckets[].Name"
	• User Policies: aws iam list-user-policies
	• Role Policies: aws iam list-role-policies
	• Group policies: aws iam list-group-policies
	• Create user: aws iam create-user
	21. This concludes the demonstration of escalating IAM user privileges by exploiting a misconfigured user policy.
	22. Close all open windows and document all acquired information.
Question 19.3.1.1
Escalate IAM user privileges by exploiting a misconfigured user policy. Which aws command will list all user policies?
aws iam list-user-policies

PreviousNext

From <https://labclient.labondemand.com/Instructions/63c28e91-a756-4f02-8772-09792bbc3769> 


![image](https://github.com/user-attachments/assets/58843a84-614c-4187-8a1e-a488237ae337)
