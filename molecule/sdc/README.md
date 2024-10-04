# Single Docker Container

This is a [Molecule][01] scenario called `sdc` for *Single Docker Container*.

## 🚀 Motivation

This scenario can be used to test [Ansible][02] roles on a single [Docker][03] container running locally.

## 🧰 Dependencies

This scenario was tested and is confirmed to work properly when using the dependencies that are listed [here][04].

Besides the dependencies mentioned above, make sure to have [Docker][05] installed on your machine.

## ⚡ Quick start

1. From within your Ansible role directory, execute the commands below:

    1. To create the container defined in the `molecule.yml` file:

        ```bash
        molecule create -s sdc
        ```

    1. To execute the tasks defined in the `converge.yml` file on the created container:

        ```bash
        molecule converge -s sdc
        ```

    1. To connect to the container defined in the `molecule.yml` file, use the container's name:

        ```bash
        molecule login -s sdc -h debian-12
        ```

    1. Finally, to destroy the container:

        ```bash
        molecule destroy -s sdc
        ```

    For additional information about the commands above, check the *Test sequence commands* section available in the [Molecule documentation][06].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://www.docker.com/
[04]: https://github.com/fernandobohrer/ansible-venv
[05]: https://docs.docker.com/engine/install/
[06]: https://ansible.readthedocs.io/projects/molecule/usage/#test-sequence-commands
