# Ansible Role: Logrotate

This role installs the Log rotation utility `logrotate` via the system package manager.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

``` yaml
---
logrotate_configure_system: false
logrotate_configure_apps: true

logrotate_config_system:
  blocks: []
  #   - pattern: /var/log/apache2/*.log
  #     rotate_files: 8
  #     frequency: daily
  #     missingok: true
  #     compress: true
  #     notifyempty: true
  #     sharedscripts: true
  #     create:
  #       mode: 0640
  #       user: www-data
  #       group: www-data
  #     postrotate: |
  #       systemctl reload apache2

logrotate_config_apps:
  []
  # - app_name: apache2
  #   blocks:
  #     - pattern: /var/log/apache2/*.log
  #       rotate_files: 8
  #       frequency: daily
  #       missingok: true
  #       compress: true
  #       notifyempty: true
  #       sharedscripts: true
  #       create:
  #         mode: 0640
  #         user: www-data
  #         group: www-data
  #       postrotate: |
  #         systemctl reload apache2
```

## Dependencies

None.

## Example Playbook

```yaml
    - hosts: all
      roles:
        - role: delta4x4.monitoring.logrotate
          vars:
          # .. (see above)
```

## License

Proprietary

## Author Information

This role was created in 2023 by [Maximilian Gindorfer](https://fmj.dev).
