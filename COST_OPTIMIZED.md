# `cost-optimized` branch (mrgaryg fork)

Differences from `ansible/product-demos` `main`, to lower EC2 cost for demo labs:

| Change | Detail |
|---|---|
| Instance sizes | RHEL/AL2023/Mattermost/Gitea: `t3a.small`. Windows and Kafka: `t3a.medium` (were all `t3.medium`). |
| Single Windows host | *Deploy Cloud Stack* no longer creates `aws_win1` (Windows Core); `aws-dc` is the only Windows VM. *Destroy Cloud Stack* and the patch/snapshot/restore templates default to `_hosts_windows: aws-dc`. |

Upstream docs under `cloud/docs/` still describe the five-VM stack; they are left unchanged to keep merges from upstream clean.

**Use it in a lab:** before running *APD | Multi-demo setup*, set the AAP project **Ansible Product Demos** to
`https://github.com/mrgaryg/product-demos.git`, branch `cost-optimized`, and sync it. Workflows are built from this
branch at setup time, and blueprints are read at run time.

**Override per run:** launching *Cloud | AWS | Create VM* with `create_vm_aws_instance_size` still wins over the blueprint.

**Stay current:** `git fetch upstream && git merge upstream/main` on this branch.
