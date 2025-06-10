# k8s_lab

![k8s_lab drawio](https://github.com/user-attachments/assets/5c041008-e3b1-4406-a715-a07975706e61)

Master lab setup playbooK (including assertions): </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/site.yml </br>

Individual Lab Setup Playbooks: </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_sys_prereq.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_instl_pkg.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_instl_crio.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_sys_assert.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_instl_cluster.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_cluster_assert.yml  </br>

Master helm setup playbook (including a sample testing case): </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/site.yml </br>

Individual Helm Setup Playbooks: </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/add_repos.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/instl_plugins.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/enable_autocompl.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/test_helm.yml  </br>

Helm Deployment Playbooks: </br>
ansible-playbook -i inventory/hosts.yml -l nginx_host playbooks/deploy/create_nginx.yml </br>
ansible-playbook -i inventory/hosts.yml -l apache_host playbooks/deploy/create_apache.yml </br>

Cleanup Deployment
ansible-playbook -i inventory/hosts.yml -l cleanup_host playbooks/cleanup/cleanup.yml -e "{rn: my_rn, ns: my_ns, crds: [crd1, crd2, ...]" </br>
i.e.: </br> 

ansible-playbook -i inventory/hosts.yml -l cleanup_host playbooks/cleanup/cleanup.yml \
-e "{\"rn\": \"kube-prometheus-stack\", \"ns\": \"k8s-monitoring\", \"crds\": [\"alertmanagers.monitoring.coreos.com\", \"podmonitors.monitoring.coreos.com\", \"prometheuses.monitoring.coreos.com\", \"prometheusrules.monitoring.coreos.com\", \"servicemonitors.monitoring.coreos.com\", \"thanosrulers.monitoring.coreos.com\"]}" </br>

Install k8s Monitoring Stack
ansible-playbook -i inventory/hosts.yml -l mon_stack_host playbooks/mon/instl_mon_stack.yml --ask-vault-pass </br>
