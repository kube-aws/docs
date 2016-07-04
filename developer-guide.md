# Build

Clone the [kube-aws repository](https://github.com/kubernetes-incubator/kube-aws) to the appropriate path under the GOPATH.

```
$ export GOPATH=$HOME/go
$ mkdir -p $GOPATH/src/github.com/kubernetes-incubator/
$ git clone git@github.com:kubernetes-incubator/kube-aws.git $GOPATH/src/github.com/kubernetes-incubator/kube-aws
```

Run `make build` to compile kube-aws locally.

This depends on having:

* golang &gt;= 1.8

The compiled binary will be available at `bin/kube-aws`.

## Run Unit Tests

```bash
make test
```

## Reformat Code

```bash
make format
```

# Modifying Templates

The various templates are located in the `core/controlplane/config/templates/` and the `core/nodepool/config/templates/` directory of the source repo. `go generate` is used to pack these templates into the source code. In order for changes to templates to be reflected in the source code:

```bash
make build
```



