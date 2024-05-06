# Ansible Role set and check CI facts

sets and checks facts from environment variables or from terraform state on control host

## Dependencies

The role depends on terraform and a backend configuration for terraform including the credentials (possibly set by environment variables) in the folder the playbook is executed (not the folder of the playbook).

The role uses `community.general.json_query`.

## Role Variables

<!-- markdownlint-disable MD033 -->
| group | variable | default | description |
| --- | --- | ---| --- |
| facts | set_and_check_ci_facts_required_vars | `[]` | <p>the list of variables to get from environment or terraform state</p>The variables are looked up from<br /><ul><li>the environment variables with the same name as in the list, but in upper cases (if `set_and_check_facts_from_terraform_state` is `false`)</li><li>the outputs of the terraform state with the same name as in the list (if `set_and_check_facts_from_terraform_state`)</li></ul>If the variable could not be set and is not in `set_and_check_ci_facts_non_required_vars`, ansible.builtin.failed is used to fail. |
| facts | set_and_check_ci_facts_non_required_vars | `[]` | the list of variables not to check if set or not |
| facts | set_and_check_ci_facts_required_env_vars | `[]` | <p>the list of variables to get from environment</p>The variables are looked up from the environment variables with the same name as in the list, but in upper cases. |
| facts | set_and_check_ci_facts_non_required_env_vars | `[]` | the list of variables not to check if set or not (subset of `set_and_check_ci_facts_required_env_vars`) |
| facts | set_and_check_ci_facts_required_tf_vars | `[]` | <p>the list of environment variables `TF_VAR_*` to get from the environment</p>The ansible variables are named without prefix `TF_VAR_` and assumed to be named with exact case. |
| facts | set_and_check_ci_facts_non_required_tf_vars | `[]` | the list of variables `TF_VAR_*` not to check if set or not (subset of `set_and_check_ci_facts_required_tf_vars`) |
| control | set_and_check_ci_facts_from_terraform_state | `false` | if the facts in `set_and_check_ci_facts_required_vars` should be read from terraform state instead from environment |
| control | set_and_check_ci_facts_terraform_command | `'terraform'` | <p>the terraform cmd</p>This can be used for GitLab ci to set to `gitlab-terraform` or for specifying a terraform command by full path. |
| control | `set_and_check_ci_facts_terraform_dir` | `'.'` | the director to `chdir` before executing `set_and_check_ci_facts_terraform_command` |
| debug | `set_and_check_ci_facts_print_terraform_state` | `false` | if the terraform state should be printed (only output values) |

<!-- markdownlint-enable MD033 -->
