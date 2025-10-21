# Ansible Molecule scenarios

This repository contains a set of [Molecule][01] scenarios that can be used to test [Ansible][02] roles during their development lifecycle.

## 🚀 Motivation

The use of [Molecule][01] scenarios allows for Ansible roles to be tested on multiple instances and distributions, on multiple virtualization providers and on multiple Docker containers.

## 🧰 Dependencies

These [Molecule][01] scenarios were tested and are confirmed to work properly when using the dependencies that are listed [here][03].

For details about any specific dependencies for the different scenarios, please check the relevant information in the `README.md` file within each scenario folder.

## ⚡ Quick start

The easiest way to integrate these Molecule scenarios to your Ansible role is to clone this repository to the `molecule` folder in your Ansible role path.

After cloning this repository, you might want to remove the `.git` directory associated to this project since you are probably interested in this project's files themselves and probably not on the repository itself.

From within your Ansible role directory, execute:

```bash
git clone --depth 1 https://github.com/fernandobohrer/ansible-molecule-scenarios.git molecule ; rm -rf molecule/.git
```

## 📑 Molecule scenarios details

The following Molecule scenarios are available:

- `mdc` or *Multiple Docker Containers*
- `mvb` or *Multiple Vagrant Boxes*
- `sdc` or *Single Docker Container*
- `svb` or *Single Vagrant Box*

For details about how to get started with the different scenarios, please check the relevant information in the `README.md` file within each scenario folder.

## 📝 License

This project is licensed under the terms of the [MIT license][04].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://github.com/fernandobohrer/ansible-venv
[04]: /LICENSE
