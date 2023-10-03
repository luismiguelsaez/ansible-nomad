
## Create nodes

```bash
for node in nomad-01 nomad-02 nomad-03; do
  multipass launch -n $node -c 1 -d 20G -m 512M --cloud-init ./cloud-init.yaml 22.04
done
```

## Configure nodes

```bash
ansible-playbook playbook.yaml
```

## Join nodes

```bash
multipass exec nomad-02 nomad server join 192.168.64.102
multipass exec nomad-03 nomad server join 192.168.64.102
```

## Check servers

http://192.168.64.102:4646/ui/servers

