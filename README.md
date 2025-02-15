# ansible-playbook-ubuntu-docker

```sh
export X_TAG="vm_tag_${INSTANCE_NAME}"
ansible "${X_TAG}" --inventory ./inventory/aws_ec2.yml -m ping \
  --extra-vars "ansible_connection=aws_ssm" \
  --extra-vars "ansible_aws_ssm_region=${AWS_REGION}"
```
