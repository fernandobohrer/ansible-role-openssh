# Multiple Docker Containers

This is a [Molecule][01] scenario called `mdc` for *Multiple Docker Containers*.

## 🚀 Motivation

This scenario can be used to test [Ansible][02] roles on multiple [Docker][03] containers running locally.

## 🧰 Dependencies

This scenario was tested and is confirmed to work properly when using the dependencies that are listed [here][04].

Besides the dependencies mentioned above, make sure to have [Docker][05] installed on your machine.

## ⚡ Quick start

1. From within your Ansible role directory, execute the commands below:

    1. To create the containers defined in the `molecule.yml` file:

        ```bash
        molecule create -s mdc
        ```

    1. To execute the tasks defined in the `converge.yml` file on the created containers:

        ```bash
        molecule converge -s mdc
        ```

    1. To connect to any container defined in the `molecule.yml` file, use the container's name:

        ```bash
        molecule login -s mdc -h debian-12
        ```

    1. Finally, to destroy the containers:

        ```bash
        molecule destroy -s mdc
        ```

    For additional information about the commands above, check the *Test sequence commands* section available in the [Molecule documentation][06].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://www.docker.com/
[04]: https://github.com/fernandobohrer/ansible-venv
[05]: https://docs.docker.com/engine/install/
[06]: https://ansible.readthedocs.io/projects/molecule/usage/#test-sequence-commands
