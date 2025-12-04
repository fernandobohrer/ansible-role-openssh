# Multiple Vagrant Boxes

This is a [Molecule][01] scenario called `mvb` for *Multiple Vagrant Boxes*.

## 🚀 Motivation

This scenario can be used to test [Ansible][02] roles on multiple [Vagrant][03] boxes running locally.

## 🧰 Dependencies

This scenario was tested and is confirmed to work properly when using the dependencies that are listed [here][04].

Besides the dependencies mentioned above, make sure to have [Vagrant][05] and [VirtualBox][06] installed on your machine.

## ⚡ Quick start

1. From within your Ansible role directory, execute the commands below:

    1. To create the virtual machines defined in the `molecule.yml` file:

        ```bash
        molecule create -s mvb
        ```

    1. To execute the tasks defined in the `converge.yml` file on the created virtual machines:

        ```bash
        molecule converge -s mvb
        ```

    1. To connect to any virtual machine defined in the `molecule.yml` file, use the virtual machines's name:

        ```bash
        molecule login -s mvb -h debian-13
        ```

    1. Finally, to destroy the virtual machines:

        ```bash
        molecule destroy -s mvb
        ```

    For additional information about the commands above, check the *Test sequence commands* section available in the [Molecule documentation][07].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://www.vagrantup.com/
[04]: https://github.com/fernandobohrer/ansible-venv
[05]: https://developer.hashicorp.com/vagrant/install
[06]: https://www.virtualbox.org/wiki/Downloads
[07]: https://ansible.readthedocs.io/projects/molecule/usage/#test-sequence-commands
