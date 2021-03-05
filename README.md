# ansible-3tier-app
This project creates a CI/CD pipeline using Ansible Tower Workflow Template to provision 2 environments and deploy the 3 Tier Application code to both environments.

### Configure_3TA_AWS.yml
* This playbook uses Ansible Tower AWS EC2 dynamic inventory feature to provision 3 Tier Application:
  * HAProxy on the frontend server to load balance between application servers.
  * Tomcat on the application servers.
  * PostgreSQL on the database server.
* The AWS EC2 dynamic inventory creates groups in the format AnsibleGroup_<group>, where group is replaced by the actual groups defined in the service during provisioning: apps, appdbs, frontends
