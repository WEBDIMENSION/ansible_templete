# Ansible In Docker

## 動作環境

### Local

- On Docker for Mac

### Target OS

- AlamLinux8.5
- Almalinux9.0

### Python version

```bash
# docker-compose run --rm ansible python --version
Python 3.8.13
```

### Ansible vesion

```bash
#  docker-compose run --rm ansible ansible --version
ansible [core 2.12.6]
  config file = /src/ansible.cfg
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.8/site-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.8.13 (default, May 28 2022, 14:36:46) [GCC 8.3.0]
  jinja version = 3.1.2
  libyaml = True
```

## ssh key generate

```bash
cd src/certs/<<your_project>>
ssh-keygen -b 4096 -f ansible
```

## Ansible lint

```bash
docker-compose run --rm ansible ansible-lint
```

## playbook 設定 実行

### secret.yml

` roles/{{taks_name}}/default/main/secret.yaml ` の機密情報は
`group_vars/{{host_group_name}}/secret.yml` または `host_vars` へ転記。   
`group_vars`のほうが優先される。

Read -> hosts/ansible_deno/README.md

### 機密情報の暗号化

### vault pass

```bash
echo 'vault_password_file = ./vaultpass' > ansible.cfg
cp valtpass.sample valtpass
echo 'your_vault_password' > vaultpass
```   

#### 暗号化

```bash
docker-compose run ansible ansible-vault encrypt group_vars/{{ group_name }}/secret.yml
```

#### 復号化

```bash
docker-compose run ansible ansible-vault decrypt group_vars/{{ group_name }}/secret.yml
```

