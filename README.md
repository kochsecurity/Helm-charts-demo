Pre-requisites:

1) Kubernetes cluster
2) Helm installed

Helpful helm commands:

```helm show values [releasename]``` used to see what values are configurable in a chart

```helm get manifest [releasename]``` used to show the manifest deployed to the cluster, helful for debugging

```helm install [releasename] . ``` installs the chart with the releasename you provided

```helm upgrade [releasename] . ``` upgrades the release showing release number

#### Helm diff

Install Helm diff plugin

```helm plugin install https://github.com/databus23/helm-diff```


```helm diff revision myapp 1 3``` Where ```1``` and ```3``` are the revision number you want to enter to see differences in this scenario