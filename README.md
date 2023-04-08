# Ansible Role Cron

### Creating Cron Jobs
```yaml
cron_jobs:
  - name: "Every minute job"
    minute: "*"
    user: "ubuntu"
    job: "/usr/bin/sh /home/ubuntu/script >> /some/location/script.log 2>&1"
  - name: "Run Job at 2:15PM Every Saturday"
    minute: "15"
    hour: "14"
    day: "SAT"
    job: |-
      su www-data -c "/usr/bin/php7.4 /some/location/php >> {{ cron_log_base_dir }/application/php.log 2>&1"
```

### Optional Log Directories
```yaml
create_cron_log_base_dir: yes
cron_log_base_dir: "/var/log/cron"
cron_log_dir:
  - dir_name: sys
    owner: ubuntu
  - dir_name: application
    owner: www-data
    group: dev
```
