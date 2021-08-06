# Ansible Role set and check CI facts

sets and checks facts from environment variables on control node

## Role Variables

### `set_and_check_facts_from_environment_required_vars`: `[]`

the list of variables to get from environment

The variables are looked up from the environment variables with the same name as in the list, but in upper cases.
If the environment variable is not set and not in `set_and_check_facts_from_environment_non_required_vars`, ansible.builtin.failed is used to fail.

### `set_and_check_facts_from_environment_non_required_vars`: `[]`

the list of variables not to check if set

### `set_and_check_facts_from_environment_required_tf_vars`: `[]`

the list of environment variables `TF_VAR_*` to get from the environment

The ansible variables are name without prefix `TF_VAR_` and assumed to be name with exact case.

### `set_and_check_facts_from_environment_non_required_tf_vars`: `[]`

the list of variables `TF_VAR_*` not to check if set
