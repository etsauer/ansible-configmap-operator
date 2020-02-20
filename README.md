# ConfigMap Ansible Operator

This is a test project to see whether we can write an Ansible Operator for ConfigMaps.

To test:

1. Install the Operator SDK per the [Ansible Operator user guide](https://github.com/operator-framework/operator-sdk/blob/master/doc/ansible/user-guide.md)
2. Clone this repo.
3. Copy `roles/configmap` to `/opt/ansible/roles`: `sudo mkdir -p /opt/ansible/roles && sudo cp -r roles/configmap/ /opt/ansible/roles/configmap`.
4. Create a namespace: `kubectl create namespace cm-test`
5. Run `operator-sdk run --local --namespace cm-test`
6. Create a ConfigMap, and check the logs to see that it triggered the operator: `kubectl apply -f deploy/examples/sample-cm-1.yaml -n cm-test`
7. Update the ConfigMap, and check the logs to see that it triggered again: `kubectl apply -f deploy/examples/sample-cm-1.yaml -n cm-test`
