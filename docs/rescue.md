# Save and Load rescue configuration into device

The `config_manager/rescue` function provides a means to save a know good running configuration
as a rescue configuration and rollback the current device configuration to rescue configuration
when required.

The `rescue` function provides some configurable options when rescuing the
configuration on the remote device.  See the `How to use this function`
section for different example of how to rescue configuration on network devices.

## How to use this function

The examples below demonstrate how to use this function in a playbook.

## How to save a rescue configuration checkpoint

Below is an example of how to call the `config_manager/rescue` function to mark the
current running configuration as rescue config.

```
- hosts: network

  roles:
    - name: ansible-network.config_manager
      function: rescue
      config_manager_set_rescue: True
```

### How to load the rescue configuration

The `config_manager/rescue` function also provides support to rollback the current running
configuration to a rescue configuration when required

In order to load the resuce configuration, the function as before but adds the
value `config_manager_load_rescue_config: yes` to the playbook to indicate that the configuration should
be rollbacked to te the resuce configuration.

Note: Take caution when doing rescue configuration load that you do not
inadvertently replace your access to the device.

```
- hosts: network

  roles:
    - name: ansible-network.config_manager
      function: rescue
      config_manager_load_rescue_config: True
```

## How to delete a rescue configuration checkpoint

Below is an example of how to call the `config_manager/rescue` function to delete the
previously set rescue configuration.

```
- hosts: network

  roles:
    - name: ansible-network.config_manager
      function: rescue
      config_manager_delete_rescue: True
```

## Arguments

### config_manager_set_rescue

This setting indicates whether or not the to set the current running
configuration as the rescue configuration.

The default value is `False`

### config_manager_load_rescue_config

This setting indicates whether or not to replace the current configuration
with the rescue configuration.

The default value is `False`

### config_manager_delete_rescue

This setting indicates whether or not the to delete the rescue configuration
checkpoint that is already set.

The default value is `False`

## Notes

None
