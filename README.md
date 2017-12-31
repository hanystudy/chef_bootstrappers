# chef_bootstrappers

As title mean.

## Usage

This tutorial will be based on hosted chef server, for other types of deployment please check official docs for chef. And make sure you have box set similar to [vagrantfile](https://github.com/hanystudy/vagrantfiles).

Install cookbook and dependencies:

```
berks install
```

Upload cookbook using berks:

```
berks upload
```

Upload role to chef server, you have to run this command again, once you edit json files for specific role:

```
knife role from file roles/elastic_node.json
```

Bootstrap node with marking as specific role:

```
knife bootstrap 192.168.55.2 -r 'role[elastic_node]' --ssh-user vagrant --sudo --identity-file ~/vmkeys/centos7 --node-name node1-elasticsearch
```

Manually run chef-client:

```
knife ssh 'name:node1-elasticsearch' 'sudo chef-client' --ssh-user vagrant --identity-file ~/vmkeys/centos7 --manual-list
```
