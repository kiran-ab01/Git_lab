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


# Additional Tools Used for Code Review & Collaboration
Snippets,Wikis,Web IDE.

GitLab Projects are housed within Groups

Groups can have any number of Subgroups

![image](https://github.com/user-attachments/assets/2e95d0b1-236e-421f-b21c-016b7297d9df)

# Gitlab projects and group visibilty

1.private: For private projects only members of the project or group can: clone the project, users with guest can't clone the project and private groups can have only private subgroups/

2.Internal: For internal any authenticated users including users with guest role can: clone the project, only internal memebers can view the intrnal content and external members can't clone the projects and private groups can have intrtnal and  private subgroups.

3.Public: for public projects users with not authenticated and users with guest role can: clone the project and public group can have public,internal and private subgroups.

# GitLab CI/CD: Key Ingredients
1 .gitlab-ci.yml -> It specified the stages, jobs, and actions that you want to perform. Think of the YAML file as the brains, and the runner as the body.

2. install and configure a Gitlab Runner: a file written in Go, will run the jobs specified in the YAML file using an API to communicate with GitLab. 

# .gitlab-ci.yml
Global keywords: 
1.Defult: 
Each default keyword is copied to every job that doesn’t already have it defined. If the job already has a keyword defined, that default is not used.

Supported values: after_script,artifacts,before_script,cache,hooks,id_tokens,image,interruptible,retry,services,tags.
![image](https://github.com/user-attachments/assets/9d6ec6db-76a8-4084-b8b7-366c04339fc4)

2. include:
   Use include to include external YAML files in your CI/CD configuration. You can split one long .gitlab-ci.yml file into multiple files to increase readability.

   Supported values:include:component,include:local,include:project,include:remote,include:template.include:inputs,include:rules,include:integrity.

   a.include:component: 
include:
- component: $CI_SERVER_FQDN/my-org/security-components/secret-detection@1.0

b.include:local:
include:local to include a file that is in the same repository and branch as the configuration file containing the include keyword.
include:
  - local: '/templates/.gitlab-ci-template.yml'

c. include:project:
To include files from another private project on the same GitLab instance, use include:project and include:file

include:
  - project: 'my-group/my-project'
    ref: main

    




