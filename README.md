# Ansible sample with workflow

This provides ansible sample with [github action workflow](https://github.com/kumvijaya/ansible-samples/blob/main/.github/workflows/ansible-workflow.yml).

## Workflow steps
- **Checkout**: Checksout the repository
- **Show changed files**: Shows the list of changed ansible playbook yaml files. This uses [tj-actions](https://github.com/tj-actions/changed-files).
- **Show diff of changed files**: Shows file diffs for changed ansible playbook yaml files. This uses [git diff](https://git-scm.com/docs/git-diff).
- **Lint ansible files**: Lints the changed ansible playbook yaml files using [ansible-lint-action](https://github.com/ansible/ansible-lint-action). This uses [Lint config](https://ansible-lint.readthedocs.io/configuring/) defined in *.config/ansible-lint*
- **Dry-run**: Dryrun the changed ansible playbook yaml files. This uses [check/dryrun](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_checkmode.html#:~:text=In%20check%20mode%2C%20Ansible%20runs,before%2Dand%2Dafter%20comparisons) mode with [ansible CLI](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide).
This also uses the [Inventory config (hosts)](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) defined in *deploy/hosts*