# Ansible

Выполните vagrant up, чтобы создать следующие виртуальные машины:

ansible-node-master - 192.168.56.10 - Ubuntu 18.04

ansible-node-ubuntu - 192.168.56.110 - Ubuntu 18.04

ansible-node-debian - 192.168.56.120 - Debian 10

ansible-node-centos7 - 192.168.56.130 - CentOS 7

ansible-node-centos8 - 192.168.56.140 - CentOS 8

---

К ansible-node-master подключается папка data/ansible

У ansible-node-master устанавливается и обновляется vbox guest additions, без него не получится подключить общую папку из Vagrantfile

У остальных машин установка vbox guest additions отключена из-за проблем с совместимостью

Все виртуальные машины имеют 1 cpu / 1Gb RAM

---

Для создания директорий ролей ansible можно выполнить скрипт create_dir_for_role_ansible.sh

---

Запуск playbook:

ansible-playbook -i inventory <name_playbook>

Example:

ansible-playbook -i inventory testroles_vm1.yml

