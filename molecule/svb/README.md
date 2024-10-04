# Single Vagrant Box

This is a [Molecule][01] scenario called `svb` for *Single Vagrant Box*.

## 🚀 Motivation

This scenario can be used to test [Ansible][02] roles on a single [Vagrant][03] box running locally.

## 🧰 Dependencies

This scenario was tested and is confirmed to work properly when using the dependencies that are listed [here][04].

Besides the dependencies mentioned above, make sure to have [Vagrant][05] and [VirtualBox][06] installed on your machine.

## ⚡ Quick start

1. From within your Ansible role directory, execute the commands below:

    1. To create the virtual machine defined in the `molecule.yml` file:

        ```bash
        molecule create -s svb
        ```

    1. To execute the tasks defined in the `converge.yml` file on the created virtual machine:

        ```bash
        molecule converge -s svb
        ```

    1. To connect to the virtual machine defined in the `molecule.yml` file, use the virtual machines's name:

        ```bash
        molecule login -s svb -h debian-12
        ```

    1. Finally, to destroy the virtual machine:

        ```bash
        molecule destroy -s svb
        ```

    For additional information about the commands above, check the *Test sequence commands* section available in the [Molecule documentation][07].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://www.vagrantup.com/
[04]: https://github.com/fernandobohrer/ansible-venv
[05]: https://developer.hashicorp.com/vagrant/install
[06]: https://www.virtualbox.org/wiki/Downloads
[07]: https://ansible.readthedocs.io/projects/molecule/usage/#test-sequence-commands
