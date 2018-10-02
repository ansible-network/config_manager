===============================
config_manager
===============================

v2.6.1
======

Major Changes
-------------

- Adds scm support to allow the role to automatically retrieve
the device configuration from scm.
- Move the config file load into config_manager.


v2.6.0
======

New Functions
-------------

- NEW `get` for retrievign the current active configuration
- NEW `load` loads a configuration onto a network device
- NEW `save` saves the current active configuration to non-volatile storage


Major Changes
-------------

- Initial release of the `config_manager` role.
