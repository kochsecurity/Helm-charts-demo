Pre-requisites:

1) Kubernetes cluster
2) Helm installed

Helpful helm commands:

```helm show values [releasename]``` used to see what values are configurable in a chart

```helm get manifest [releasename]``` used to show the manifest deployed to the cluster, helful for debugging

```helm install [releasename] . ``` installs the chart with the releasename you provided

```helm upgrade [releasename] . ``` upgrades the release showing release number

#### Helm diff

First, Install Helm diff plugin

```helm plugin install https://github.com/databus23/helm-diff```


```helm diff revision myapp 1 3``` Where ```1``` and ```3``` are the revision number you want to enter to see differences in this scenario

```helm diff upgrade <release> <releaseChartversion>```

In this xxample, ```helm diff upgrade artifactory https://charts.jfrog.io/artifactory-107.33.12.tgz``` helm will output the changes that will occure by comparing the current release currently install to the upgrade we are making and seeing what has changed.


## Helm Repo Branch

We generally want to create another branch to host our helm repo

create helm package in Charts directory

```helm package helm -d ../charts```

This command successfully creates a chart based on specfications entered in your chart.yaml file. So, in this case, we have:
```Successfully packaged chart and saved it to: ../charts/northstar-1.0.0.tgz```

We will need to generate our index.yaml file using another helm utility ```helm repo index ../charts``` directory, generates your ```index.yaml``` file

```
apiVersion: v1
entries:
  northstar:
  - apiVersion: v2
    appVersion: 0.0.1
    created: "2022-04-29T23:15:40.262261-04:00"
    description: A Helm chart to deploy northstar version 1.0.0
    digest: 2e66b732313493bd7a0539a18c0d8c35c5ed25bd2e7611ffa72557629ed0f42a
    name: northstar
    type: application
    urls:
    - northstar-1.0.0.tgz
    version: 1.0.0
generated: "2022-04-29T23:15:40.259637-04:00"
```

Since we now have a package file (.tgz) and an index.html file, we can now publish this publickly for others to consume.

we will need a server that can serve static files like github pages and s3.


