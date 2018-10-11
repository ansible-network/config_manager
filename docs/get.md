# Get configuration from device

The Config Manager role provides a function that will connect to the remote
network device and retrieve, by default, the current device active (running)
configuration.  The configuration will be returned to the calling playbook as a
fact in the device host facts.  The returned text based configuration can be
accessed via `config_manager.config` fact.

## How to use this function

The examples below demonstrate how to use this function in a playbook.

### How to get the device configuration

To retrieve the current active configuration from the device, simply include
the `ansible-network.config_manager` role and execute the `get` function.  

Below is an example of calling the `get` function from the playbook.

```
---
- hosts: network
  gather_facts: false
  roles:
    - name ansible-network.config_manager
      function: get

```

The example playbook above will return the current active configuration for
each device in the inventory group `network`.

### How to get the device configuration from tasks

The `get` function can also be includes in the playbook `Tasks:` section and
executed as part of the list of tasks.  Below is an example of how to retrieve
the configuration using tasks.

```
---
- hosts: network
  gather_facts: false

  tasks:
    - name: get active configuration from device
      include_role:
        name: ansible-network.config_manager
        tasks_from: get

    - name: display the device configuration to stdout
      debug:
        var: config_manager.config.split('\n')
```

The example playbook above will retrieve the current running configuration and
then display the configuration contents to stdout.

## Arguments

None

## Notes

None
