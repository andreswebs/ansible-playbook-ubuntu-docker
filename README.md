# ansible-playbook-ubuntu-docker

## Usage

```sh
ansible-galaxy install -r requirements.yml
```

## Example: Hetzner

```sh
export HCLOUD_TOKEN
export ANSIBLE_REMOTE_USER="root"
export ANSIBLE_PRIVATE_KEY_FILE="${HOME}/.ssh/id_ed25519_hetzner"
```

```sh
./playbook.yml -e custom_hosts=example
```

## Example: AWS

```sh
export X_TAG="vm_tag_${INSTANCE_NAME}"
export X_AWS_SSM_BUCKET_NAME
export AWS_REGION
export AWS_PROFILE
```

```sh
ansible "${X_TAG}" --inventory ./inventory/aws_ec2.yml -m ping \
  --extra-vars "ansible_connection=aws_ssm" \
  --extra-vars "ansible_aws_ssm_region=${AWS_REGION}" \
  --extra-vars "ansible_aws_ssm_bucket_name=${X_AWS_SSM_BUCKET_NAME}"
```

```sh
./playbook.yml \
  --extra-vars "custom_hosts=${X_TAG}" \
  --extra-vars "ansible_connection=aws_ssm" \
  --extra-vars "ansible_aws_ssm_region=${AWS_REGION}" \
  --extra-vars "ansible_aws_ssm_bucket_name=${X_AWS_SSM_BUCKET_NAME}"
```

## Authors

**Andre Silva** - [@andreswebs](https://github.com/andreswebs)

## License

[Unlicense](UNLICENSE)
