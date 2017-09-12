# ansible-macos-ssd
A Ansible role to optimize _only_ non Apple SSDs.

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-ssd.svg)](https://travis-ci.org/feffi/ansible-macos-ssd) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-ssd/total.svg)](https://github.com/feffi/ansible-macos-ssd) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-ssd.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-ssd) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-ssd.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-ssd) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-ssd.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-ssd) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-ssd/blob/master/LICENSE)

## Requirements
- Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-macos-ssd.git
  name: feffi.macos-ssd
```

## Role Variables
All role based variables are listed below, along with default values:

```yaml
macos_ssd:
  # Enable TRIM. See http://en.wikipedia.org/wiki/TRIM
  trim: false

  # Enable Sudden Motion Sensor technology. See https://en.wikipedia.org/wiki/Sudden_Motion_Sensor
  sms: false

  # Disable file access time. See https://en.wikipedia.org/wiki/Access_time
  noatime: false

  # where to set the noatime
  noatime_plist: "/Library/LaunchDaemons/com.noatime.plist"
```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_ssd:
          trim: true
          sms: true
          noatime: true
      roles:
        - { role: feffi.macos-ssd }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-ssd,
            macos_ssd: {
              trim: true,
              sms: true,
              noatime: true
            }
          }
```
