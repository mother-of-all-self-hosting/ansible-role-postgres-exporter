# Ansible Role Postgres Exporter

This is an [Ansible](https://www.ansible.com/) role which installs [Postgres Exporter](https://github.com/prometheus-community/postgres_exporter) to run as a [Docker](https://www.docker.com/) container wrapped in a systemd service.

This role *implicitly* depends on:

- [`com.devture.ansible.role.playbook_help`](https://github.com/devture/com.devture.ansible.role.playbook_help)
- [`com.devture.ansible.role.systemd_docker_base`](https://github.com/devture/com.devture.ansible.role.systemd_docker_base)


> **NOTE**: check [defaults/main.yml](./defaults/main.yml) to see full list of config options
>

You should create a seperate user in your postgres instance to collect the metrics and NOT use the superuser. You will need to grant this user (`postgres_exporter` in the example) special permissions

```SQL
GRANT pg_monitor to postgres_exporter;
```

# Integrate with Grafana

You can use the dasboard [9628](https://grafana.com/grafana/dashboards/9628-postgresql-database/) to visualize the data in Grafana.

![A grafana dashboard showing connection data, commits to the database and more](assets/grafana_screenshot.jpeg)