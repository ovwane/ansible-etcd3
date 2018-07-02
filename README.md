# ansible-etcd3

A role which installs and manages a clustered etcd 3.x on CentOS 7

```shell
pipenv install ansible
```

Ansible ssh need [sshpass](https://sourceforge.net/projects/sshpass/)

macOS install [githu issue sshpass](https://github.com/ansible-tw/AMA/issues/21)

```shell
brew create https://sourceforge.net/projects/sshpass/files/sshpass/1.06/sshpass-1.06.tar.gz --force

brew install sshpass
```



## Requirements

* ansible 2.4

## Example

modify inventories, then

```shell
ansible-playbook -i inventories/dev/hosts deploy-etcd3.yml -k
```

## 查看集群状态

检查集群是否健康，在任一节点执行：

```shell
etcdctl \
  --ca-file=/etc/etcd/ssl/ca.crt \
  --cert-file=/etc/etcd/ssl/client.crt \
  --key-file=/etc/etcd/ssl/client.key \
  --endpoints=https://10.8.8.11:2379,https://10.8.8.12:2379,https://10.8.8.13:2379 \
  cluster-health
```

```shell
etcdctl \
  --ca-file=/etc/etcd/ssl/ca.crt \
  --cert-file=/etc/etcd/ssl/client.crt \
  --key-file=/etc/etcd/ssl/client.key \
  --endpoints=https://10.8.8.11:2379,https://10.8.8.12:2379,https://10.8.8.13:2379 \
  member list
```