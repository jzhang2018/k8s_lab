# k8s_lab

Master lab setup playbooK: </br>
ansible-playbook -i hosts site.yml </br>

Individual Playbook: </br>
ansible-playbook -i inventory/hosts playbooks/setup/k8s_sys_prereq.yml </br>
ansible-playbook -i inventory/hosts playbooks/setup/hosts k8s_instl_pkg.yml  </br>
ansible-playbook -i inventory/hosts playbooks/setup/hosts k8s_instl_crio.yml </br>
ansible-playbook -i inventory/hosts playbooks/setup/hosts k8s_sys_assert.yml  </br>
ansible-playbook -i inventory/hosts playbooks/setup/hosts k8s_instl_cluster.yml  </br>
ansible-playbook -i inventory/hosts playbooks/setup/hosts k8s_cluster_assert.yml  </br>
