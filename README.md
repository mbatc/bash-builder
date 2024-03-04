# Bash Builder

Sometimes I just want to use bash, sometimes I need to store variables, paths, etc., so sometimes I use **Bash Builder**.

## What does it do?

* **set_config_var**: Save per project persistent variables.
* **get_config_var**: Read per project persistent variables.
* **configure_var**: Prompt the user to input a variable.
* **configure_path**: Prompt the user to input a file path.
* **setup_repo**: Prompt the user to configure a git repository that the project is dependent on.
* Not much else...

## How do I use it?

1. Create a new shell script to do something (e.g. configure a project).
2. Use functions provided by bash-builder in your script. You might create a `setup.sh` script to configure some variables, paths, repos, etc.
```sh
# Write a variable
set_conf_var "my-first-var" "A value"

# Read a stored variable
MY_VAR="$(get_conf_var "my-first-var")"

# Prompt user for a variable (if not set). 
configure_var "my-variable" "The default value for my-variable"

# Prompt user to configure the path to a repo. 
setup_repo "repo-path-var"  "https://github.com/mbatc/Adder" "branch-to-clone"

echo "Bash builder cloned 'https://github.com/mbatc/Adder' to '$(get_conf_var "repo-path-var")'"
```
3. Run the `setup.sh` script in a project directory using **bash-builder**
```sh
bash-builder /path/to/project /path/to/project/setup.sh
```
3. (optional) You could also reuse `setup.sh` with a different project.
```sh
bash-builder /path/to/my-other-project /path/to/project/setup.sh
```
