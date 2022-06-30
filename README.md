Vagrant Virtualbox setup for Consul with Envoy
========================

An exercise on installing Consul with Envoy for VM service mesh

## Download vagrant from Vagrant website

```
https://www.vagrantup.com/downloads.html
```

## Install Virtual Box

```
https://www.virtualbox.org/wiki/Downloads
```

## Download CentOS 7 box
```
vagrant init centos/7
```

## Bring up nodes

```
vagrant up consul-node
```

## Access VM

```
vagrant ssh consul-node
```

## Stop nodes

```
vagrant halt consul-node
```

## Destroy nodes

```
vagrant destroy consul-node
```
