# Ansible Role: Promtail

This role installs Grafana's `Promtail` which is an additional utility used alongside `Loki`, a distributed log aggregation system.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

``` yaml
promtail_version: 2.8.2
promtail_dist_url:
  "https://github.com/{{ _promtail_repo }}/releases/download/v{{ promtail_version }}\
  /promtail-linux-{{ _go_arch }}.zip"
promtail_custom_checksum: ""

promtail_loki_server_url: http://localhost:3100
promtail_positions_path: "/var/lib/promtail"

promtail_config_path: /etc/promtail
promtail_config_file_path: "{{ promtail_config_path }}/config.yml"
promtail_config_expand_env: false

promtail_system_group: promtail
promtail_system_user: "{{ promtail_system_group }}"

promtail_skip_install: false
promtail_install_dir: /opt/promtail
primtail_install_tmp_dir: /tmp/promtail

promtail_systemd_service: promtail

promtail_config_server:
  http_listen_port: 9494
  http_listen_address: 0.0.0.0
  log_level: info

promtail_config_clients:
  url: "{{ promtail_loki_server_url }}/loki/api/v1/push"
  # basic_auth:
  #   username: "{{ inventory_hostname }}"
  #   password: testingpassword

promtail_config_scrape_configs:
  []
  # - job_name: system
  #   static_configs:
  #     - targets:
  #         - localhost
  #       labels:
  #         job: varlogs
  #         __path__: /var/log/*log

promtail_config_positions:
  filename: "{{ promtail_positions_path }}/positions.yaml"

promtail_config_target_config:
  sync_period: "10s"

```

## Dependencies

None.

## Example Playbook

```yaml
    - hosts: all
      roles:
        - role: delta4x4.monitoring.promtail
          vars:
          # .. (see above)
```

## License

Proprietary

## Author Information

This role was created in 2023 by [Maximilian Gindorfer](https://fmj.dev).
