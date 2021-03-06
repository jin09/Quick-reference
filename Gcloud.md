# GCLOUD QUICK COMMANDS

### Check the authenticated account that gcloud is currently using

```
gcloud auth list
```

### Check the current project which is set on the gcloud where all the changes will be made

```
gcloud config list project
```

### Setup new gcloud account on CLI

```
gcloud init
```

### Check all configuration set on gcloud CLI

```
gcloud config list --all
```

### Deploy app using gcloud

```
gcloud app deploy [path/to/app.yaml]
```
or go to the dir where your `app.yaml` is and hit the command  

```
gcloud app deploy
```

### Deploy indexes on google cloud  

```
gcloud app deploy index.yaml
```

### Logout the gcloud google account

```
gcloud auth revoke
```
