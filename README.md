<!--

---
lang: american
---
-->

[![Build Status](https://travis-ci.org/cw-ansible/cw.isc-dhcp-client.svg?branch=master)](https://travis-ci.org/cw-ansible/cw.isc-dhcp-client)
[![Tweet this](http://img.shields.io/badge/%20-Tweet-00aced.svg)](https://twitter.com/intent/tweet?tw_p=tweetbutton&via=renard_0&url=https%3A%2F%2Fgithub.com%2Fcw-ansible%2Fcw.isc-dhcp-client&text=Install%20and%20configure%20%23DHCP%20client%20using%20%23Ansible)
[![Follow me on twitter](http://img.shields.io/badge/Twitter-Follow-00aced.svg)](https://twitter.com/intent/follow?region=follow_link&screen_name=renard_0&tw_p=followbutton)


# DHCP client configuration

This roles ensures the `isc-dhcp-client` package is installed. It also
deploys an DHCP hook `hostname` which is able to change the server hostname
according its IP address.
 
## Usage

Simply call the `isc-dhcp` role from a playbook.

## Configuration

None

## Hostname configuration

The DHCP hook in `/etc/dhcp/dhclient-exit-hooks.d/hostname` is called every
time a DHCP request is run. It looks for the host name from:
- the DHCP server as an option;
- the reverse (PTR) of the new IP address;
- finally the hostname is set from the host IP address changing the dots to
  dashes.


For this command to success, it should be linked to a file which name is:

	hostname-INTERFACE

With `INTERFACE` as the name of the network interface to use to setup the
hostname, such as `eth0` (`hostname-eth0`).

This ansible role uses `ansible_default_ipv4.alias` as default interface to
setup hostname.


## Copyright

Author: Sébastien Gross `<seb•ɑƬ•chezwam•ɖɵʈ•org>` [@renard_0](https://twitter.com/renard_0)

License: WTFPL, grab your copy here: http://www.wtfpl.net
