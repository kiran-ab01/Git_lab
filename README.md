# Git_lab

Intigrate gitlab with other applications:

When you use a self-signed certificate to integrate GitLab with external applications, you might encounter SSL certificate errors.

Configure SSL for a Linux package installation:

Starting from version 17.5, GitLab uses OpenSSL 3.

Configure HTTPS:

# 1.To enable HTTPS:

Edit /etc/gitlab/gitlab.rb:

Set the external_url to your domain. Note the https in the URL:

external_url "https://gitlab.example.com"

# 2.Disable the Let’s Encrypt integration:
letsencrypt['enable'] = false

# 3. Create the /etc/gitlab/ssl directory and copy your key and certificate there:
sudo mkdir -p /etc/gitlab/ssl

sudo chmod 755 /etc/gitlab/ssl

sudo cp gitlab.example.com.key gitlab.example.com.crt /etc/gitlab/ssl/

# Change the default HTTPS port
If you need to use an HTTPS port other than the default (443), specify it as part of the external_url:

Edit /etc/gitlab/gitlab.rb:

external_url "https://gitlab.example.com:2443"

sudo gitlab-ctl reconfigure

# Adding trusted root certificates to the server
If you want to send or receive messages signed by root authorities and these authorities are not installed on the server, you must add a trusted root certificate manually.

Linux (Ubuntu, Debian): 

To Add: 
Copy your CA to dir /usr/local/share/ca-certificates/

Use command: sudo cp foo.crt /usr/local/share/ca-certificates/foo.crt

Update the CA store: sudo update-ca-certificates

To Remove:

Remove your CA.

Update the CA store: sudo update-ca-certificates --fresh

# gitlab intigrate with jira

1. Import your Jira project issues to GitLab
# GitLab offers two Jira integrations.
1. Jira issues integration
Prerequisites:
For Jira Cloud: You must have a Jira Cloud API token and the email address you used to create the token.

For Jira Data Center or Jira Server: jira username and password or token
   
3. Jira development panel
   
For Jira Cloud, use the GitLab for Jira Cloud app developed and maintained by GitLab.

For Jira Data Center or Jira Server, use the Jira DVCS connector developed and maintained by Atlassian.

# Migrating from Jenkins to GitLab
https://www.youtube.com/watch?v=RlEVGOpYF5Y

# GitLab Workflow With Jira Issues And Jenkins Pipelines
https://www.youtube.com/watch?v=Jn-_fyra7xQ

# GitHub Integration with git lab
GitLab provides an integration for updating the pipeline statuses on GitHub. This is especially useful if using GitLab for CI/CD only.

# Configure GitLab as an OAuth 2.0 authentication identity provider
use GitLab as an OAuth 2 authentication identity provider by adding the following types of OAuth 2 application to an instance:

User owned applications.
Group owned applications.
Instance-wide applications.

# Auto Devops in GitLab
https://www.youtube.com/watch?v=0Tc0YYBxqi4

# GitLab Runner
GitLab Runner is an application that works with GitLab CI/CD to run jobs in a pipeline.

# GitLab
GitLab is a git-based completely integrated DevSecOps platform for the complete software development lifecycle.

# What is Git?
Free open source Version Control System (VCS)
Tracks changes in source code during software development

three most well-known version control tools (also known as revision control systems) are Git, Subversion (SVN), and Mercurial.

![image](https://github.com/user-attachments/assets/76228da5-18c4-4efd-ae95-e7270c09c477)

![image](https://github.com/user-attachments/assets/c5f3abc1-5724-4f53-ac44-14bc68aae22a)


