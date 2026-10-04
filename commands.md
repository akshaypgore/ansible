ansible-playbook -i inventories/staging/hosts base.yml -u akshay --tags common --check
ansible-playbook --syntax-check site.yml
ansible-inventory -i inventories/staging/hosts --list
ansible-playbook -i inventories/staging/hosts base.yml -u akshay --check
ansible-playbook -i inventories/staging/hosts db.yml -u akshay --check
ansible-playbook -i inventories/staging/hosts site.yml -u akshay --check (for entire infra setup)
ansible-playbook site.yml --list-tasks
ansible-inventory -i inventories/staging/hosts --graph
ansible k8s-etcd-server -i inventories/staging/hosts -m ping -u akshay