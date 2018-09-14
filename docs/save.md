# Save active configuration to startup

For network platforms that support saving the current active (running)
configurationt to non-volatile storage, the Config Manager `save` function can
be invoked.  This function will issue the save command on the target platform
regardless of whether or not the active configuration has changed.  

If the target platform does not support the `save` function, then it should
simply return a NOOP.

## How to save the active configuration

To save the current active configuration to the startup configuration simply
invoke the `save` function on the target device.  There are no additional 
configuration options for this funnction.

Below is an example of calling the `save_config` function from the playbook.

```
- hosts: network

  roles:
    - name ansible-network.arista_eos
      function: save
```

## Arguments

None

## Notes

None
