# Ansible_demo

## Rootアカウントから`ansible_user`作成

conohaなどの VPS では初期アカウントはRootのみ   
AWSのような ec2-user などある場合は必要なし

```bash
# init
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/init site.yml -l init -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/init site.yml -l init -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/init site.yml -l init 
````

### Debug

テスト的なtaks用

```bash
# debug
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/debug -l debug site.yml  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/debug -l debug site.yml  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/debug -l debug site.yml
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/debug -l debug site.yml -t os_version   
````

### Lamp

Lamp環境作成 (site.yml確認)

- Apache
- PHP
- MySQL
- Postgresql

```bash
#lamp
cd src/certs/{{your_project}}
ssh-keygen -b 4096 -f ansible
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t lamp  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t lamp  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t lamp  
```

### Lamp

Lemp環境作成 (site.yml確認)

- Nginx
- PHP
- MySQL
- Postgresql

```bash
#lemp
cd src/certs/your_project
ssh-keygen -b 4096 -f ansible
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t lemp  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t lemp  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t lemp  
```

### sshd

```bash
# sshd
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/sshd -l sshd site.yml -t sshd  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/sshd -l sshd site.yml -t sshd  -C 
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/sshd -l sshd site.yml -t sshd
```

### Nginx

```bash
#Nginx
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t nginx  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t nginx  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t nginx  
```

### Apache

```bash
#httpd
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t httpd  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t httpd  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t httpd  
```

### PHP

```bash
# php
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t php  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t php  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t php  
# or
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t php  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t php  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t php  
```

### MySQL

```bash
# MySQL
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t mysql8  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t mysql8  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t mysql8  
# or
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t mysql8  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t mysql8  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t mysql8  
```

### Postgresql

```bash
# Postgresql
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t postgresql  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t postgresql  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lamp -l lamp site.yml -t postgresql  
# or
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t postgresql  -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t postgresql  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/lemp -l lemp site.yml -t postgresql  
```

### SererMonitor

```bash
# Monitor
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t monitor  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t monitor
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t glances  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t glances 
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t bpytop  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t bpytop
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t bashtop  -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/staging -l monitor site.yml -t bashtop
```

### Docker

```bash
# docker
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/docker -l docker site.yml -C -vvv
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/docker -l docker site.yml -C
docker-compose run --rm ansible ansible-playbook -i hosts/ansible_demo/docker -l docker site.yml
```

### ssh 接続

```bash
# Root login (First time)
ssh root@{{host or ip}} -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no
# ansible user login
ssh ansible@{{host or ip}} -i ./src/certs/ansible_demo/ansible -p 22 -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no  -o ControlMaster=auto -o ControlPersist=60s
```

## Ansible lint

```bash
docker-compose run --rm ansible ansible-lint
```

#### 暗号化

```bas
docker-compose run ansible ansible-vault encrypt group_vars/ansible_demo/secret.yml
```

#### 復号化

```bash
docker-compose run ansible ansible-vault decrypt group_vars/ansible_demo/secret.yml
```
