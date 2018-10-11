# Load configuration into device

The Config Manager role provides a function that will load configuration onto a
remote network device.  The `load` function will accept the device
configuration as either text or a source file.  

The `load` function provides some configurable options when pushing the
configuration to the remote device.  See the `How to use this function`
section for different example of how to push configurations to network devices.

## How to use this function

The examples below demonstate how to use this function in a playbook.

## How to load and merge a configuration

Loading a configuration onto a target device is fairly simple and
straightforward.  By default, the `load` function will merge the contents of
the provided configuration file with the configuration running on
the target device.  

Below is an example of how to call the `load` function.

```
- hosts: network
  gather_facts: false

  roles:
    - name: ansible-network.config_manager
      function: load
      config_manager_file: device.cfg
```

The example playbook above will simple load the contents of `device.cfg` onto the
target network devices and merge the configurations.

## How to load and replace a configuration

Similar to the merge capabilities, this role also supports replacing the
current device configuration on the remote target.  In order to tell the `load`
function to replace the entire configure on the remote device with the provided
configuration, set the `config_manager_replace` value to True.

```
- hosts: network
  gather_facts: false

  roles:
    - name: ansible-network.config_manager
      function: load
      config_manager_file: device.cfg
      config_manager_replace: True
```

The example playbook above will load the file specified by
`config_manager_file` and replace the configuration on the remote device.

## Arguments

### config_manager_file

This setting provides the path to the configuration file to use as input for
loading a configuration onto a remote device.  This setting can either be a
full path to the configuration file or a relative to the playbook root path.
The `config_manager_file` setting is mutually exclusive with the
`config_manager_text` setting.

The default value is `None`

### config_manager_text

This setting can be used to pass the device configuration file text in directly
instead of using a file.  This configuration text is then passed directly to
the platform for implementation.  The `config_manager_text` setting is mutually
exclusive with the `config_manager_file` setting.

The default value is `None`


### config_manager_replace

When this value is set to True, the provided configuration text will replace
the current configuration on the target node.  If this value is set to False,
then the configuration provided is merged with the configuration running on the
target device.

The default value is `False`

## Notes

None
