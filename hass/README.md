Home Assistant
==============

An Ansible Role that installs [Home Assistant](https://www.home-assistant.io/) on Debian/Ubuntu. Tested with Debian 9 Stretch.

Requirements
------------

* ansible >= 2.2

Role Variables
--------------

- **hass_user**: The linux user Home Assistant is running under. Defaults to `hass`
- **hass_virtualenv**: The directory the virtual environment for Home Assistant gets installed to. Defaults to `/opt/hass`.
- **hass_config**: The directory the configuration for Home Assistant is stored in. Defaults to `/home/hass/.homeassistant`.
- **hass_w1** Enables One Wire for Raspberry Pis. Usefull if you connect One Wire sensors directly to your Raspberry Pi and want to add them to Home Assistant. By default it is disabled (`false`).
- **hass_apt_packages** List of apt packages whoch should be installed in addition. Might be useful if you use Home Assistant components which depend on additional packages (e.g. [FRITZ!Box Net Monitor](https://www.home-assistant.io/components/sensor.fritzbox_netmonitor/)). By default it is not defined.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: hass
  roles:
    - hass
```

```yaml
- hosts: hass
  vars:
    hass_user: "pi"
    hass_virtualenv: "/srv/hass"
    hass_w1: true
    hass_apt_packages:
      - libxslt-dev
      - libxml2-dev
      - python3-lxml
  roles:
     - hass
```

License
-------

Apache 2.0

Author Information
------------------

Johannes Krausmueller (johannes@krausmueller.de)
Website: https://www.krausmueller.de
