# Apache Control Ansible Role

This Ansible role is designed to manage the Apache HTTP Server on Linux systems that use `systemd`. The role provides functionality to check the current status of Apache, start it if it's not running, and stop it if it is running.

## Requirements

There are no prerequisites or dependencies required to use this role apart from Ansible.

## Role Variables

This role does not define any variables for configuration.

## Dependencies

No dependencies on other Ansible roles.

## Files Structure

- **tasks**: Contains the main tasks for the role.
    - `main.yml`: The main entry point for the role that includes other task files.
    - `start.yml`: Contains tasks to start Apache.
    - `stop.yml`: Contains tasks to stop Apache.
- **handlers**:
    - `main.yml`: Contains handlers, which may be used to restart Apache if it's required.
- `ansible.cfg`: The Ansible configuration file.
- `hosts`: The inventory file where you define your group of servers.

## Role Tasks

The tasks provided by this role are defined in `tasks/main.yml`. Here's a rundown of what each task does:

### Check if Apache is running

This task checks the status of the Apache service using the `systemctl status httpd` command. It registers the output in a variable named `apache_status`. The task is designed not to mark the play as changed or fail under normal circumstances, except when Apache is inactive or dead and when it is not running despite an active status being reported.

### Debug Apache running status

If Apache is found to be running, a debug message "Apache is currently running." will be output.

### Start Apache if it's not running

If Apache is not running, this task will execute `systemctl start httpd` to start the Apache service. After attempting to start Apache, it will output "Apache has been started."

### Stop Apache if it's running

Similarly, if Apache is running, the role will execute `systemctl stop httpd` to stop the service. A debug message "Apache has been stopped." will be output to confirm the action.

## Handlers

The `handlers/main.yml` file contains handlers that can restart Apache when notified by other tasks in the playbook that changes requiring a restart have occurred.

## Configuration

You should adjust the `ansible.cfg` and `hosts` file according to your requirements and environment.

## Example Playbook

Include this role in your Ansible playbook:

```yaml
- hosts: all
  roles:
    - apache_control

```

## Usage

Execute the role by running the playbook through the ansible-playbook command:
To start Apache:
```
ansible-playbook start_apache_playbook.yml
```
To stop Apache:
```
ansible-playbook stop_apache_playbook.yml
```

## Contributing

Contributions to this role are welcome! Please fork the repository, make your changes, and submit a pull request.

## Created by Nipuna Vancha
