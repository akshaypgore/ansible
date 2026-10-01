1. ansible-playbook -i inventories/staging/hosts base.yml -u akshay --tags common --check
2. ansible-playbook --syntax-check site.yml
3. ansible-inventory -i inventories/staging/hosts --list
4. ansible-playbook -i inventories/staging/hosts base.yml -u akshay --check
4. ansible-playbook -i inventories/staging/hosts db.yml -u akshay --check
5. ansible-playbook -i inventories/staging/hosts site.yml -u akshay --check (for entire infra setup)