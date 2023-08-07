# Ansible cheat sheet

 


| Category | Command/Option | Explanation |
|---|---|---|
| General | `ansible --version` | Display the version of Ansible installed. |
| General | `ansible -m ping all` | Ping all hosts to check if they are reachable. |
| General | `ansible -m shell -a 'free -m' all` | Run the 'free -m' shell command on all hosts. |
|---|---|---|
| Playbooks | `ansible-playbook playbook.yml` | Run the playbook named `playbook.yml`. |
| Playbooks | `ansible-playbook -i inventory.ini playbook.yml` | Run a playbook with a specified inventory file. |
| Playbooks | `ansible-playbook playbook.yml --syntax-check` | Perform a syntax check on the playbook. |
| Playbooks | `ansible-playbook playbook.yml --start-at-task='taskname'` | Start the playbook at the specified task. |
| Playbooks | `ansible-playbook playbook.yml --list-hosts` | List all hosts the playbook will run against. |
| Playbooks | `ansible-playbook playbook.yml --list-tasks` | List all tasks the playbook will execute. |
| Playbooks | `ansible-playbook playbook.yml --step` | Execute the playbook interactively, asking for confirmation at each step. |
| Playbooks | `ansible-playbook playbook.yml --check` | Do a dry run of the playbook without making actual changes. |
| Playbooks | `ansible-playbook playbook.yml --diff` | Show differences in files when running the playbook. |
| Playbooks | `ansible-playbook playbook.yml --tags "tag1,tag2"` | Run only the tasks tagged with tag1 and tag2. |
| Playbooks | `ansible-playbook playbook.yml --skip-tags "tag3"` | Skip tasks tagged with tag3. |
| Playbooks | `ansible-playbook playbook.yml --limit servers` | Limit the playbook execution to the group 'servers'. |
| Playbooks | `ansible-playbook playbook.yml --extra-vars "version=1.2.3"` | Run the playbook with extra variables. |
| Playbooks | `ansible-playbook playbook.yml --forks=5` | Set the number of parallel processes to 5. |
| Playbooks | `ansible-playbook playbook.yml -v` | Run the playbook in verbose mode. `-vvv` and `-vvvv` can be used for more verbosity. |
| Playbooks | `ansible-playbook playbook.yml --check --diff` | Dry-run the playbook and show file differences. |
|---|---|---|
| Roles | `ansible-galaxy init role_name` | Initialize a new role structure with the specified name. |
| Roles | `ansible-galaxy install role_name` | Install an Ansible role. |
|---|---|---|
| Vault | `ansible-vault create vault.yml` | Create a new encrypted file. |
| Vault | `ansible-vault view vault.yml` | View an encrypted file. |
| Vault | `ansible-vault edit vault.yml` | Edit an encrypted file. |
| Vault | `ansible-vault decrypt vault.yml` | Decrypt an encrypted file. |
| Vault | `ansible-vault encrypt vault.yml` | Encrypt a file. |
| Vault | `ansible-vault rekey vault.yml` | Change the password on a vault file. |
| Vault | `ansible-vault encrypt_string --name 'var_name' 'string'` | Encrypt a string and output it in a format ready for use with Ansible. |
| Vault | `ansible-playbook playbook.yml --ask-vault-pass` | Run a playbook and prompt for the vault password. |
| Vault | `ansible-playbook playbook.yml --vault-password-file vault.pass` | Run a playbook using a file containing the vault password. |
| Vault | `ansible-vault encrypt_string --stdin-name 'var_name'` | Read the string from stdin and encrypt it. |
| Vault | `ansible-vault encrypt --vault-id dev@prompt vars.yml` | Encrypt a file using a prompt for the vault password. |
| Vault | `ansible-playbook playbook.yml --vault-id dev@prompt` | Run a playbook using a prompt for the vault password. |
|---|---|---|
| Configuration | `ansible-config list` | List all configuration options. |
| Configuration | `ansible-config dump` | Show the current configuration. |
| Configuration | `ansible-config view` | View the current Ansible configuration. |
| Configuration | `ansible-config dump --only-changed` | Dump configuration items that have changed from the default. |
| Configuration | `ansible-config set ANSIBLE_HOST_KEY_CHECKING=False` | Set a specific configuration item. |
| Configuration | `ansible-config unset ANSIBLE_HOST_KEY_CHECKING` | Unset a specific configuration item. |
|---|---|---|
| Console | `ansible-console` | Start an interactive console for executing Ansible tasks. |
| Console | `ansible-console -i inventory.ini` | Start an interactive console using a specific inventory. |
|---|---|---|
| Modules | `ansible-doc -l` | List available modules. |
| Modules | `ansible-doc module_name` | Get documentation for a specific module. |
|---|---|---|
| Inventory | `ansible-inventory --list -y` | List the inventory in YAML format. |
| Inventory | `ansible-inventory --graph` | Show a graph of the inventory. |
| Inventory | `ansible -i inventory.ini all -m ping` | Use a specific inventory file and ping all hosts. |
| Inventory | `ansible-inventory --host hostname` | Display all variables for a specific host. |
| Inventory | `ansible-inventory --playbook-dir . --graph` | Display a graph of the inventory from the current directory. |
| Inventory | `ansible -i 'localhost,' -c local -m ping` | Ping localhost using local connection and ad-hoc inventory. |
| Inventory | `ansible-inventory --list --yaml` | List inventory in YAML format. |
|---|---|---|
| Pull | `ansible-pull -U git_url` | Pull a Git repository of Ans
| Pull | `ansible-pull -U git_url` | Pull a Git repository of Ansible configurations on the target host. |
|---|---|---|
| Galaxy | `ansible-galaxy collection init my_namespace.my_collection` | Initialize a new collection with the given namespace and name. |
| Galaxy | `ansible-galaxy collection build` | Build an Ansible collection package ready for distribution. |
| Galaxy | `ansible-galaxy collection install my_namespace.my_collection` | Install an Ansible collection from Galaxy. |
| Galaxy | `ansible-galaxy role init my_role` | Initialize a new role with the given name. |
| Galaxy | `ansible-galaxy role install my_role` | Install an Ansible role from Galaxy. |
| Galaxy | `ansible-galaxy list` | List installed roles and collections. |
| Galaxy | `ansible-galaxy collection install -r requirements.yml` | Install collections from a requirements file. |
| Galaxy | `ansible-galaxy role install -r requirements.yml` | Install roles from a requirements file. |
| Galaxy | `ansible-galaxy collection publish ./namespace-collection-1.0.0.tar.gz --api-key=your_token` | Publish a collection to Galaxy using an API token. |
| Galaxy | `ansible-galaxy role init --role-skeleton skeleton my_role` | Initialize a new role with a specified role skeleton. |
|---|---|---|
| Modules | `ansible localhost -m file -a "path=/tmp/test state=touch"` | Create a new file on the local host using the file module. |
| Modules | `ansible localhost -m package -a "name=vim state=present"` | Install a package on the local host using the package module. |
| Modules | `ansible localhost -m command -a "uptime"` | Run a command on the local host using the command module. |
| Modules | `ansible localhost -m user -a "name=testuser state=absent"` | Remove user 'testuser' from the local host using the user module. |
| Modules | `ansible localhost -m service -a "name=httpd state=restarted"` | Restart the 'httpd' service on the local host using the service module. |
| Modules | `ansible localhost -m copy -a "src=/etc/hosts dest=/tmp/hosts"` | Copy '/etc/hosts' to '/tmp/hosts' on the local host using the copy module. |
| Modules | `ansible localhost -m file -a "path=/tmp/test state=absent"` | Remove file '/tmp/test' on the local host using the file module. |
| Modules | `ansible localhost -m apt -a "name=nginx state=latest"` | Install the latest version of 'nginx' on the local host using the apt module (Debian-based systems). |







Remember to always use these commands with care and understand their implications, especially in a production environment. Also, the options and flags of Ansible commands can be combined in various ways to achieve the desired results. For a more in-depth understanding, always refer to the official Ansible documentation.