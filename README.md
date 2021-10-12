# Ansible Role: fail2ban

An Ansible Role that installs Fail2Ban on Asymworks servers.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values if applicable (see `defaults/main.yml`):

```yaml
f2b_ignore_ips: ['127.0.0.1/8', '::1']
f2b_ban_time: 10m
f2b_find_time: 10m
f2b_max_retries: 5
```

Sets up the basic Fail2Ban configuration including passlisted IPs and durations.

```yaml
f2b_email: true
f2b_email_dest: "root@{{ ansible_fqdn }}"
f2b_email_sender: "root@{{ ansible_fqdn }}"
f2b_email_mta: sendmail
```

Fail2ban email notification settings.  A `sendmail` compatible MTA must be installed (note the mSMTP Ansible Role symlinks `msmtp` to `sendmail` automatically).

```yaml
f2b_action: mwl
```

Fail2ban action when a jail is triggered.  The default bans the IP address, sends a report, and includes logging context in the report email.

```yaml
f2b_ssh_enabled: true
f2b_ssh_name: sshd
```

Whether to enable Fail2Ban for the SSH server, optionally using a different jail name (e.g. `dropbear` instead of `sshd`).

## Role Facts

None

## Dependencies

None

## Example Playbook

    - hosts: all
      roles:
        asymworks.baseline
        asymworks.fail2ban

## License

MIT / BSD

## Author

This role was created in 2019 by Jonathan Krauss for managing home network infrastructure.
