# Single AWS Instance

This is a [Molecule][01] scenario called `sai` for *Single AWS Instance*.

## 🚀 Motivation

This scenario can be used to test [Ansible][02] roles on a single [EC2 instance][03] on [AWS][04].

## 🧰 Dependencies

This scenario was tested and is confirmed to work properly when using the dependencies that are listed [here][05].

## ⚡ Quick start

1. In a local terminal session, set the `AWS_ACCESS_KEY_ID`, `AWS_SECRET_KEY`, `AWS_REGION` and `SUBNET_ID` environment variables accordingly to your infrastructure on AWS:

    ```bash
    export AWS_ACCESS_KEY_ID=AKIA...
    export AWS_SECRET_KEY=ABCD...
    export AWS_REGION=us-east-1
    export SUBNET_ID=subnet-0123456789abcdefg
    ```

    Make sure to use a subnet that is configured to auto-assign public IPv4 addresses to the EC2 instances. For more details, check [here][06].

1. From within your Ansible role directory, execute the commands below:

    1. To create the instance defined in the `molecule.yml` file:

        ```bash
        molecule create -s sai
        ```

    1. To execute the tasks defined in the `converge.yml` file on the created instance:

        ```bash
        molecule converge -s sai
        ```

    1. To connect to the instance defined in the `molecule.yml` file, use the instance's name:

        ```bash
        molecule login -s sai -h debian-12
        ```

    1. Finally, to destroy the instance:

        ```bash
        molecule destroy -s sai
        ```

    For additional information about the commands above, check the *Test sequence commands* section available in the [Molecule documentation][07].

[01]: https://ansible.readthedocs.io/projects/molecule/
[02]: https://www.ansible.com/
[03]: https://aws.amazon.com/ec2/
[04]: https://aws.amazon.com/
[05]: https://github.com/fernandobohrer/ansible-venv
[06]: https://docs.aws.amazon.com/vpc/latest/userguide/modify-subnets.html#subnet-public-ip
[07]: https://ansible.readthedocs.io/projects/molecule/usage/#test-sequence-commands
