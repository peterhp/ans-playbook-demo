# Ansible Practice

## Roles

### Role: create-instance

- Variables
  * inst_region
  * inst_image (ami-01da99628f381e50a)
  * inst_type (t2.micro)
  * inst_group (sg-06e96344c81b81790)
  * inst_subnet (subnet-6831e40d)
  * inst_key_name
  * inst_name

- Output
  * aws-insts
  * aws-inst
  * aws_inst_summary

### Role: install-toolkit

- Variables
  * toolkit

### Role: build-spring-boot

- Variables
  * app_name
  * app_repo
  * app_branch (master)

- Output
  * app_jar_path

- Dependencies
  * Role: install-toolkit

### Role: deploy-spring-boot

- Variables
  * app_path (/apps/boot)
  * app_log_path (/apps/boot/logs)
  * app_name
  * app_version (default)
  * app_file ({{app_name}}.jar)
  * app_local_file (no)
  * app_base_url (http://localhost:8080)

- Dependencies
  * Role: install-toolkit

## Web Server Structure

```
apps/
  |-- boot/
  |    |-- ans-web-demo.jar
  |    |-- logs/
  |         |-- application.log
  |-- rc.init
  |-- rc.verify
```
