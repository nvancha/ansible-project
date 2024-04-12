# Apache Control Ansible Role

This Ansible role provides a simple way to manage the Apache HTTP Server on systems using `systemd`. With this role, you can check the status of Apache, start it if it's not running, or stop it if it is.

## Requirements

There are no prerequisites required to run this role apart from Ansible itself.

## Role Variables

Currently, this role does not use any variables. It's designed to work with the default configuration of Apache on systems that use `systemd` for service management.

## Dependencies

There are no dependencies on other roles.

## Files Structure

- **tasks**: Contains the main tasks for the role.
    - `main.yml`: The main entry point for the role that includes other task files.
    - `start.yml`: Contains tasks to start Apache.
    - `stop.yml`: Contains tasks to stop Apache.
- **handlers**:
    - `main.yml`: Contains handlers, which may be used to restart Apache if it's required.
- `ansible.cfg`: The Ansible configuration file.
- `hosts`: The inventory file where you define your group of servers.

## Example Playbook

To use this role, include it in your playbook as follows:

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
