Go to live! kata
==================================

Contained in this repo, there are some instructions for a new application that will go live in the next month!

You will need to:

1. Fork this repository.

2. Automate the creation of the infrastructure and the setup of the application.

   You have only these instructions:

   2.1 It works on Ubuntu Linux 14.04 x64

   2.2 It's based on the last version of WordPress (it will be more useful if we can parameterize the version)

   2.3 You can choose Apache, Nginx or whatever you want

   For any other issues or question you will have to ask to the developers. In this case please ask us without problems :)

3. Once deployed, the application should be secure, fast and stable. Assume that the machine is running on the public Internet and should be hardened and locked down.

4. Make any assumptions that you need to. This is an opportunity to showcase your skills, so if you want to, implement the deployment process with any additional features, tools or techniques you'd like to.

5. We are evaluating solutions based on the architecture and quality of the deployment. Show us just how beautiful, clean and pragmatic your code can be.

6. Once your solution is ready, please send us the link of your project.


**Before you run this playbook**
* rename the credentials.yml.example to credentials.yml , and populate it using your credentials
* as python boto need to be updated locally on the control machine , this playbook must be run using the `--ask-sudo-pass` option
* the RDS instance name is wpdb . If you already have one instance with this name you **must** change the *rds_name* variable


This playbook perform the following steps :
* deploy the frontend instance
* deploy the db instance
* create access group to permit access from the frontend to the DB
* create one access group to allow remote administration for the frontend instance
* deploy frontend instance (and update it)
* harden the frontend instance ( custom sshd config , fail2ban)
* deploy WordPress on the frontend instance

 *tested with ansible 2.3.0 (devel 32b7f85f6c) and ubuntu 14.04 as ansible node*


**Assumptions :**
Here the assumptions which were used in this playbook :
* fixed AZ
* default vpc
* single zone RDS


**Future improvements**
* self signed certificate => let's encrypt certificate
