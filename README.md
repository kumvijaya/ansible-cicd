# Ansible sample with workflow

This provides ansible sample for ci and cd workflows
-  [CI workflow](https://github.com/kumvijaya/ansible-samples/blob/main/.github/workflows/ansible-ci.yml)
-  [CD workflow](https://github.com/kumvijaya/ansible-samples/blob/main/.github/workflows/ansible-cd.yml).

## CI Workflow steps
- **Checkout**: Checksout the repository
- **Show changed files**: Shows the list of changed ansible playbook yaml files. This uses [tj-actions](https://github.com/tj-actions/changed-files).
- **Show diff of changed files**: Shows file diffs for changed ansible playbook yaml files. This uses [git diff](https://git-scm.com/docs/git-diff).
- **Lint ansible files**: Lints the changed ansible playbook yaml files using [ansible-lint-action](https://github.com/ansible/ansible-lint-action). This uses [Lint config](https://ansible-lint.readthedocs.io/configuring/) defined in *.config/ansible-lint*
- **Dry-run**: Dryrun the changed ansible playbook yaml files. This uses [check/dryrun](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_checkmode.html#:~:text=In%20check%20mode%2C%20Ansible%20runs,before%2Dand%2Dafter%20comparisons) mode with [ansible CLI](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide).
This also uses the [Inventory config (hosts)](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) defined in *deploy/hosts*

## CD Workflow steps
- **Checkout**: Checksout the repository
- **Show deployment files**: Shows the list of changed ansible playbook yaml files. This uses [tj-actions](https://github.com/tj-actions/changed-files).
- **Deploy**: Executes the changed ansible playbook yaml files. This uses [playbook execution](https://docs.ansible.com/ansible/latest/network/getting_started/first_playbook.html#create-and-run-your-first-network-ansible-playbook) with [ansible CLI](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide).
This also uses the [Inventory config (hosts)](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) defined in *deploy/hosts*

*Note*: Each playbook should have facts collection tasks and the task to save the output to file in *./snapshots/* folder. The output file name should be host name of the platy book run. For example *./snapshots/csr1000v-1*
- **Commit the facts file**: Commits the added/updated fact output file to current codebase. Uses [EndBug/add-and-commit](https://github.com/marketplace/actions/add-commit)