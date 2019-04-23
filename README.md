# Ansible Role: Crowstrike Falcon

Installs CrowdStrike Falcon sensor agent for endpoint protection on supported Linux hosts.


## Requirements

Use of the CrowdStrike Falcon sensor agent requires a paid license (beyond a free trial) through [CrowdStrike](https://www.crowdstrike.com).   Using this role requires that the user download the sensor package to a remote location reachable by the host and that the required customer ID be provided to the role.


## Role Variables

Below are available variables for configuring the installation and setup of the efs utils package:

```
# Installation options:
# ---
#
# The installation instructions for Falcon on linux require that the client download the sensor package
# from the Falcon console's "Sensor Downloads" screen, and place either on the host or somewhere reachable
# by the host.   The installer is also required to copy down the Customer ID Checksum (CID) from the
# "Sensor Downloads" screen for use during installation.   This role requires both of these parameters in the
# following formats:
#
# A full http/https/ftp download url to the specific package that is to be installed on the remote host.   It is
# assumed that the url has been locked down to the host or a set of hosts tied to the customer's Crowdstrike Falcon
# account.
# cs_falcon_download_url: https://my-personal-dropbox/falcon-sensor-4.x.deb
#
# CID is required for Falcon Sensor versions > 4.0.   We assume the version being installed
# is > 4.0, so providing CID is required to run this role.
# cs_falcon_cid: 12345-ABC

# The following are optional parameters:
#
# Falcon requires that a master image remove the agent ID so that instances spun up from the master get
# unique AIDs.   If installing this role on a base AMI or master image, set this flag to `true`.
cs_falcon_remove_agent_id: false
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
         - { role: huit-academictechnology-ops.ansible-role-crowdstrike-falcon, cs_falcon_download_url: https://path/to/package/falcon.deb, cs_falcon_cid: myCid123 }

License
-------

MIT/BSD

Author Information
------------------

This role was created in 2019 by Jaime Bermudez as a member of the Harvard University IT Academic Technology group.
