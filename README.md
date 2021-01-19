# Cron

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/cron/status.svg)](https://drone.osshelp.ru/ansible/cron)

Managing cron tasks via Ansible

## Example usage

```yaml
  roles:
    - role: cron
```

## Example usage with custom users jobs

```yaml
- role: cron
      cron_osshelp_jobs:
        - { name: "example osshelp job", disabled: yes, state: present, minute: 0, hour: 0, day: 1, month: 1, weekday: 1, user: root, job: "echo hello" }
      cron_user_jobs:
        - { name: "example user job", cron_mailto: root@example.com, diabled: yes, state: present, minute: 0, hour: 0, day: 1, month: 1, weekday: 1, user: root, job: "echo hello" }
        - { name: "example user job", cron_mailto: nobody@example.com, diabled: yes, state: present, minute: 0, hour: 0, day: 1, month: 1, weekday: 1, user: nobody, job: "echo hello" }
```

## Default variables values

```yaml
    state: present
    disabled: no
    user: root
    minute: '*'
    hour: '*'
    day: '*'
    month: '*'
    weekday: '*'
```

## Deploy example for backup

```yaml
  roles:
    - role: cron
      cron_path: "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
      cron_mailto: "client@osshelp.pagerduty.com"
      cron_osshelp_jobs: [{ name: "backup", minute: "15", job: "/usr/local/sbin/custom.backup" }]
```

## TODO

None, so far.
