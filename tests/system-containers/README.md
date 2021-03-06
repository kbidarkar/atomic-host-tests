This playbook tests the system containers feature provided through the atomic and runc commands

Test Cases
Core Functionality
- Verify system containers can be installed through atomic command
- Verify system containers can be uninstalled through the atomic command
- Verify user can specify name for system containers
- Verify system containers can be listed
- Verify environment variables can be pass to the container
- Verify update/rollback of system containers
- Verify commands can be run in the system container
- Verify specification of rootfs for system containers
- Verify setting RUN_DIRECTORY and STATE_DIRECTORY
- Verify system containers are started on reboot
- Verify system containers persist through reboot

Upgrade Tests
- Verify the system container persists through ostree upgrade
- Verify the system container persists through ostree rollback

Flannel & Etcd Tests
- Verify installation of flannel and etcd containers

Negative Testing
- Verify uninstalling a system container that does not exist fails
- Verify installing a system container that does not exist fails
- Verify DESTDIR, NAME, EXEC_START, EXEC_STOP, HOST_UID, and HOST_GID
  cannot be set

NOT COVERED
Upgrade Tests
- Verify the system container persists through ostree upgrade
- Verify the system container persists through ostree rollback

### Prerequisites
  - Ansible version 2.2 (other versions are not supported)

  - Configure subscription data (if used)

    If running against a RHEL Atomic Host, you should provide subscription
    data that can be used by `subscription-manager`.  See
    [roles/redhat_subscription/tasks/main.yml](/roles/redhat_subscription/tasks/main.yml)
    for additional details.

  - Configure the required variables to your liking in [tests/system-containers/vars.yml](/tests/system-containers/vars.yml).

  - Because these tests are geared towards testing upgrades and rollbacks,
    the system under test should have a new tree available to upgrade to.

### Running the Playbook

To run the test, simply invoke as any other Ansible playbook:

```
$ ansible-playbook -i inventory tests/system-containers/main.yml
```

*NOTE*: You are responsible for providing a host to run the test against and the
inventory file for that host.
