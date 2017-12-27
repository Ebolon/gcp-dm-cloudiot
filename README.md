# Using Google Cloud Deployment Manager for Google Cloud IoT

Currently the Google Cloud Deployment Manager does not allow to access the Google Cloud IoT components. To get around this circumstance it is possible to add a custom type provider with the Google Cloud IoT API endpoint.

## HowTo

### Replace [PROJECT-ID]
Replace `[PROJECT-ID]` in `iot-config.yaml` with your GCP project id.

### Add custom cloudiot type
```
gcloud beta deployment-manager type-providers create custom-gcp-cloudiot --api-options-file=options.yaml --descriptor-url="https://cloudiot.googleapis.com/\$discovery/rest?version=v1"
```

### Look up the new type
```
gcloud beta deployment-manager types list
```

## Create example iot register
```
gcloud deployment-manager deployments create testiot --config iot-config.yaml
```

## Check dashboard
https://console.cloud.google.com/iot/registries

## Delete example iot register
```
gcloud deployment-manager  deployments delete testiot
```

## Resources:
* [Adding an API as a Type Provider](https://cloud.google.com/deployment-manager/docs/configuration/type-providers/creating-type-provider)
* [Calling a Type Provider in a Configuration](https://cloud.google.com/deployment-manager/docs/configuration/type-providers/calling-type-provider)
* [REST Resource: projects.locations.registries](https://cloud.google.com/iot/docs/reference/rest/v1/projects.locations.registries)
* [deploymentmanager-samples - Big Table Template](https://github.com/GoogleCloudPlatform/deploymentmanager-samples/tree/master/examples/v2/bigtable/python)