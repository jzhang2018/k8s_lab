# k8s_lab

![k8s_lab drawio](https://github.com/user-attachments/assets/5c041008-e3b1-4406-a715-a07975706e61)

Master lab setup playbooK (including assertions): </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/site.yml </br>

Individual Lab Setup Playbooks </br>
Run pre-requisites (including local-mirror): </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/site.yml --tags pre-req </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_pre_requisites.yml </br>

Run only local-mirror (part of pre-requisites): </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/site.yml --tags local-mirror </br>

Run pre-requisites excluding local-mirror: </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_pre_requisites.yml --skip-tags local-mirror </br>

Run bootstrap: </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/site.yml --tags bootstrap </br>
ansible-playbook -i inventory/hosts.yml playbooks/setup/k8s_bootstrap_cluster.yml </br>

Master helm setup playbook (including a sample testing case): </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/site.yml </br>

Individual Helm Setup Playbooks: </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/add_repos.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/instl_plugins.yml </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/enable_autocompl.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/test_helm.yml  </br>
ansible-playbook -i inventory/hosts.yml playbooks/helm/site.yml  </br>

Helm Deployment Playbooks: </br>
ansible-playbook -i inventory/hosts.yml -l nginx_host playbooks/deploy/nginx.yml </br>

Cleanup Deployment
ansible-playbook -i inventory/hosts.yml -l cleanup_host playbooks/cleanup/cleanup.yml -e "{rn: my_rn, ns: my_ns, crds: [crd1, crd2, ...]}" </br>
i.e.: </br> 

ansible-playbook -i inventory/hosts.yml -l cleanup_host playbooks/cleanup/cleanup.yml \
-e "{\"rn\": \"kube-prometheus-stack\", \"ns\": \"k8s-monitoring\", \"crds\": [\"alertmanagers.monitoring.coreos.com\", \"podmonitors.monitoring.coreos.com\", \"prometheuses.monitoring.coreos.com\", \"prometheusrules.monitoring.coreos.com\", \"servicemonitors.monitoring.coreos.com\", \"thanosrulers.monitoring.coreos.com\"]}" </br>

Install k8s Monitoring Stack
ansible-playbook -i inventory/hosts.yml playbooks/mon/install_mon_stack.yml --ask-vault-pass </br>

Install k8s CD Tool - Argo CD
ansible-playbook -i inventory/hosts.yml -l argo_cd_host playbooks/devops/instl_argo_cd.yml </br>