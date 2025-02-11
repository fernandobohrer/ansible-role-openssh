# Ansible Role: openssh

An opinionated Ansible role that aims to enhance the [OpenSSH][01] service security.

## 🚀 Motivation

I have been using [sshaudit.com][02] and [ssh-audit][03] to audit the OpenSSH service configuration of my personal Linux boxes. It just so happens that with the default OpenSSH service configuration, there is room for some optimization.

This project combines the hardening guides available [here][04] with some other configuration changes discussed over the Internet in an easy to apply Ansible role.

## 📑 Role Variables

Check [here][05].

## 🧰 Dependencies

None.

## ⚡ Quick start

An example of how integrate this role to an Ansible playbook can be found here:

```yml
---
- name: Enhance openssh security
  hosts: all
  become: true
  gather_facts: true
  roles:
    - fernandobohrer.openssh
```

## ⚙️ Compatibility

This role was tested on and is confirmed to work with the following Linux distributions:

- `Debian 12`
- `Ubuntu 22.04`
- `Ubuntu 24.04`

Details can be found in the [Molecule][06] scenarios available in the `molecule` folder.

## ⚠️ Warning

**`ssh` is a critical service! Wrong configuration can potentially make the service fail to start, locking you out of your machines!**

This Ansible role was tested on the above mentioned Linux distributions considering their default configuration. Your environment might have a different configuration or requirements which might conflict with the options that this role uses.

With the above in mind, it is **imperative** that you familiarize yourself with what this role does and test it on non-production machines **before** applying it to machines in a production environment.

To be safe, in a dedicated terminal window connect to the target machines **before** applying this Ansible role. Your session should not be disconnected during the role execution and this way you have a terminal window available to investigate any potential issues should they happen.

Before disconnecting from the ssh session that you established before applying this role, make sure to connect to the target machines again, on a new dedicated session **after applying this Ansible role**. By using this approach you ensure that you will continue to have access to the target machines after the configuration changes are finished.

The recommended approach described above boils down to:

1. Connect to the target machines via ssh. Keep this session open.
1. Deploy the configuration changes to the target machines using this Ansible role.
1. Using a new terminal window, connect to the machines via ssh again. This will validate that you still have access to the machines after the role was applied.
    1. Assuming you were able to successfully log in to the machines after the role was applied, disconnect from the host on both sessions and you are done.
    1. If the second ssh connection fails, use the first ssh connection to investigate, troubleshoot and fix any issues. Remember to restart the ssh service after modifying any settings and to test the connection again before disconnecting from the original session.

## ❓ FAQ

1. How can I check that the configuration changes applied via this Ansible role actually enhanced my server's `ssh` security?

    1. In the [`docs` folder](docs) you can find a set of files for different Linux distributions demonstrating the differences that exist before and after applying the changes that are part of this role. To test yourself, follow the steps below:

        1. If your host exposes the `ssh` service to the Internet:
            1. Visit [sshaudit.com][02], inform your host public IP address under `Target SSH Server` and hit `Scan`.
            1. Optionally compare the results with the relevant file available in the `docs` folder of this project.
            1. Execute this role against the target machine using an Ansible playbook. Details above, under `⚡ Quick start`.
            1. Repeat the scanning process detailed above. At this stage you should see improvements in the machine's `ssh` security.
            1. Optionally compare the up to date results with the relevant file available in the `docs` folder of this project.

        1. If your host does not expose the `ssh` service to the Internet:
            1. Connect to the target host via `ssh`.
            1. Install `pipenv`: `sudo apt-get -y install pipenv` or `pip install pipenv --user`. Details can be found [here][07].
            1. As a regular user, create a `.venv` directory anywhere: `mkdir -p randomdir/.venv ; cd randomdir`.
            1. Using `pipenv`, switch to the virtual environment: `pipenv shell`.
            1. Install `ssh-audit`: `pip install ssh-audit`.
            1. Run `ssh-audit` locally using `ssh-audit --skip-rate-test localhost` and save the results for later comparison.
            1. Optionally compare the results with the relevant file available in the `docs` folder of this project.
            1. Execute this role against the target machine using an Ansible playbook. Details above, under `⚡ Quick start`.
            1. Repeat the scanning process detailed above. At this stage you should see improvements in the machine's `ssh` security.
            1. Exit the virtual environment: `exit`.
            1. Exit the `randomdir` folder that was created earlier: `cd ..`.
            1. Remove the `randomdir` directory that was created earlier: `rm -rf randomdir`.
            1. Optionally compare the up to date results with the relevant file available in the `docs` folder of this project.

1. What are the sources for the configuration options that this Ansible role implements?

    Some of the sources include:

    - *SSH Hardening Guides* by `https://sshaudit.com` available [here][04].
    - *How to configure and use OpenSSH server and client securely* by `https://infosec.mozilla.org` available [here][08].
    - *Top 20 OpenSSH Server Best Security Practices* by `https://www.cyberciti.biz` available [here][09].
    - *Why should I re-generate a server's SSH host keys?* by `https://security.stackexchange.com` available [here][10].
    - *10 Actionable SSH Hardening Tips to Secure Your Linux Server* by `https://linuxhandbook.com` available [here][11].

## 📝 License

This project is licensed under the terms of the [MIT license][12].

[01]: https://www.openssh.com/
[02]: https://sshaudit.com/
[03]: https://pypi.org/project/ssh-audit/
[04]: https://sshaudit.com/hardening_guides.html
[05]: defaults/main.yml
[06]: https://github.com/fernandobohrer/ansible-molecule-scenarios
[07]: https://pipenv.pypa.io/en/latest/installation.html
[08]: https://infosec.mozilla.org/guidelines/openssh
[09]: https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html
[10]: https://security.stackexchange.com/questions/265378/why-should-i-re-generate-a-servers-ssh-host-keys
[11]: https://linuxhandbook.com/ssh-hardening-tips/
[12]: /LICENSE
