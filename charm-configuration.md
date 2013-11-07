## Charms - Configuration files

Charms are composed of two main things: 
- metadata.yaml (description about the charm)
- hooks folder (scripts for install/start/stop the service)

metadata.yaml has the name and description of the charm and list the services it provides/requires
Example:
```
name: cf-mysql
summary: MySQL database
requires:
  cf-server:
    interface: cf-server
```

The scripts on hook folder could be written in any language (bash, python, ruby).
The most common hooks are `install`, `start` and `stop`.

`start` could be something as simple as:
```
service [service name] start 
```

Folder example:
```
/my-charm
  /hooks
    start
    stop
    install
  metadata.yaml
  config.yaml
  revision
```

`config.yaml` is an optional file that has a list of vars (and default values) to be asked to the user on the scripts, throught `config-get` command:

```
# On the script
MY_VAR=`config-get my_var`
```

```
# On config.yaml
options:
  my_var:
    default: ''
    type: string
    description: MyVar description

```
