ansible-playbook -i inventories/staging/hosts base.yml -u akshay --tags common --check
ansible-playbook --syntax-check site.yml
ansible-inventory -i inventories/staging/hosts --list
ansible-playbook -i inventories/staging/hosts base.yml -u akshay --check
ansible-playbook -i inventories/staging/hosts db.yml -u akshay --check
ansible-playbook -i inventories/staging/hosts site.yml -u akshay --check (for entire infra setup)
ansible-playbook site.yml --list-tasks
ansible-inventory -i inventories/staging/hosts --graph
ansible k8s-etcd-server -i inventories/staging/hosts -m ping -u akshay
ansible-playbook -i inventories/staging/hosts -l 'k8s-master-server[0]' k8senabled.yml -u akshay --tags common --check

# check health
etcdctl --endpoints=https://192.168.1.61:2379,https://192.168.1.62:2379,https://192.168.1.63:2379 --cacert=/etc/ssl/certs/ca.crt --cert=/etc/ssl/certs/k8s-etcd-1.crt --key=/etc/ssl/private/k8s-etcd-1-private.key --write-out=table endpoint health

# check who is leader
etcdctl --endpoints=https://192.168.1.61:2379,https://192.168.1.62:2379,https://192.168.1.63:2379 --cacert=/etc/ssl/certs/ca.crt --cert=/etc/ssl/certs/k8s-etcd-1.crt --key=/etc/ssl/private/k8s-etcd-1-private.key --write-out=table endpoint status

# check member list
etcdctl --endpoints=https://192.168.1.61:2379,https://192.168.1.62:2379,https://192.168.1.63:2379 --cacert=/etc/ssl/certs/ca.crt --cert=/etc/ssl/certs/k8s-etcd-1.crt --key=/etc/ssl/private/k8s-etcd-1-private.key --write-out=table member list

