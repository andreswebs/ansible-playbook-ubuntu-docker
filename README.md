# ansible-playbook-ubuntu-docker

## Usage

```sh
ansible-galaxy install -r requirements.yml
```

## Example: Hetzner

```sh
./playbook.yml -e custom_hosts=bot
```

## Example: AWS

```sh
export X_TAG="vm_tag_${INSTANCE_NAME}"
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
