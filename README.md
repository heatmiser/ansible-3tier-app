# ansible-3tier-app
This project creates a CI/CD pipeline using Ansible Tower Workflow Template to provision 2 environments and deploy the 3 Tier Application code to both environments.

### Configure_3TA_AWS.yml
* This playbook uses Ansible Tower AWS EC2 dynamic inventory feature to provision 3 Tier Application:
  * HAProxy on the frontend server to load balance between application servers.
  * Tomcat on the application servers.
  * PostgreSQL on the database server.
* The AWS EC2 dynamic inventory creates groups in the format <app_stack_name>_<group>, where `app_stack_name` allows for naming the three tier stack and `group` is replaced by the actual groups defined in the service during provisioning: apps, appdbs, frontends

### UpgradePostgres_3TA_AWS
* This playbook features the upgrade of the PostgreSQL database system in the 3 Tier Application. The variable `app_stack_name` allows for specifying the three tier stack that the PostgreSQL system is a member of. The variable `postgresql_target_stream` is utilized to specify the version of PostgreSQL to upgrade to. Valid values are:
- 10
- 12
- 13
