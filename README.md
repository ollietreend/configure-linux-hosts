# Configure Linux hosts

I use this [Ansible][] configuration to initialise Linux hosts how I like them (for example, when spinning up a new Linode VPS).

The [playbooks][] in this repository have been tested against [managed nodes][] running Ubuntu Server 22.04 LTS. It may also be compatible with other Ubuntu and Debian installations.

The [control node][] (the machine which executes the playbooks) must have Ansible installed. It was developed to run on macOS, and probably won't run on other operating systems without some tweaking.

## Getting started

1. Install dependencies using Homebrew

   ```
   brew bundle
   ```

2. Configure the `hosts` file

   ```
   cp hosts.example hosts
   ```

   Each line represents a managed node. Set connection properties to Ansible knows how to connect to the host.

   Learn more about [how to build your inventory][]

3. Execute the Ansible playbook

   ```
   ansible-playbook playbooks/init-host.yaml
   ```

   Note: The first time you run this on a fresh Linux installation, you'll probably need to connect with a different username (e.g. `root`). To do that, specify the `--user` option:

   ```
   ansible-playbook --user root playbooks/init-host.yaml
   ```

## Disclaimer

This is primarily intended for my own personal use. Feel free to use it, but do so at your own risk.

[Ansible]: https://docs.ansible.com/ansible/latest/index.html
[playbooks]: https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html#playbooks
[managed nodes]: https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html#managed-nodes
[control node]: https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html#control-node
[how to build your inventory]: https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
