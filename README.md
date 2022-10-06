# Ansible Role: Checkpointz

### Description
Ansible role that will install, configure and runs [Checkpointz](https://github.com/samcm/checkpointz) in Docker: An Ethereum beacon chain checkpoint sync provider

### Table of Contents
  - [Supported Platforms](#supported-platforms)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

### Supported Platforms

* MacOS
* Debian
* Ubuntu
* Redhat(CentOS/Fedora)
* Amazon

### Requirements

* Docker Latest

### Role Variables:

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file. The variables that are listed with just their ENV variable name as the description are corresponded by the ansible variable to set if you want to change it from the default which will be inserted into the config at run-time. Please refer to the checkpointz [docs](https://github.com/samcm/checkpointz#getting-started) for more information

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `checkpointz_upstream_nodes` | [] | Specify upstream beacon nodes to use. List of JSON dictionaries with "name", "address" and "dataProvider" keys. See [config](https://github.com/samcm/checkpointz#configuration)  |
| `checkpointz_version` | "latest" |  Version of checkpointz to install and run. All available versions are listed on the checkpointz [README](https://github.com/samcm/checkpointz#images) page. Omit the 'v' in the version. e.g. 1.4.0 |
| `checkpointz_user` | "checkpointz" |  User to be created to run |
| `checkpointz_group` | "checkpointz" |  Group to be created to run |
| `checkpointz_container_name` | "checkpointz" |  Docker-Compose container name |
| `checkpointz_base_dir` | "/opt/checkpointz" |  Location to store config.yaml and docker-compose.yaml on host |
| `checkpointz_listen_addr` | 5555 | Listen addr |
| `checkpointz_logging` | "debug" | Logging level |
| `checkpointz_metrics_addr` | 9090 | Logging level  |
| `checkpointz_mode` | "full" | Sync mode. Full or Light  |
| `checkpointz_caches_blocks_max_items` | 200 | Controls the amount of "block" items that can be stored by Checkpointz (minimum 3)  |
| `checkpointz_caches_states_max_items` | 5 | Controls the amount of "state" items that can be stored by Checkpointz |
| `checkpointz_historical_epoch_count` | 20 | Controls the amount of historical epoch boundaries that Checkpointz will fetch and serve |
| `checkpointz_frontend_brand_image_url` | "" | Brand Image to show on frontend |
| `checkpointz_frontend_brand_name` | "" | Brand name to show on frontend |
| `checkpointz_frontend_public_url` | "" | Public URL where frontend will be served from |

### Example Playbook

1. Default setup:
Install the role from galaxy
```
ansible-galaxy install consensys.checkpointz
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the checkpointz [releases](https://github.com/samcm/checkpointz/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: consensys.checkpointz
    vars:
      checkpointz_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


1. Install via github

```
ansible-galaxy install git+https://github.com/ConsenSys/ansible-role-checkpointz.git
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the checkpointz [releases](https://github.com/samcm/checkpointz/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: ansible-role-checkpointz
    vars:
      checkpointz_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


### License

Apache


### Author Information

Consensys, 2022