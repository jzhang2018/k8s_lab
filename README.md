# k8s_lab

ansible-playbook -i hosts k8s_sys_prereq.yml
ansible-playbook -i hosts k8s_instl_crio.yml
ansible-playbook -i hosts k8s_instl_pkg.yml
ansible-playbook -i hosts k8s_instl_cluster.yml

TODO: playbook to verify or assert

