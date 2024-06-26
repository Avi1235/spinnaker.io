---
title: "Pin an Environment"
linkTitle: "Pin an Environment"
weight: 10
description: >
  Pin an environment to an artifact version so that environment doesn't change.
---

You can pin an environment to a specific artifact version to ensure that all resources in the environment stay on that version.
Until the pin is removed, that environment won't change to a new version of the artifact.


### Pinning via the API

To create a pin via the API you'll need the application name, the name of the environment you want to pin, the reference for your artifact (defined in your delivery config, defaulted to the artifact name), and the version you'd like to pin to.
The request needs to have a body that contains [this information](https://github.com/spinnaker/gate/blob/master/gate-core/src/main/groovy/com/netflix/spinnaker/gate/model/manageddelivery/EnvironmentArtifactPin.java).
Here's an example:

`POST /managed/application/{application}/pin`

with body:
```json

{
  "targetEnvironment": "test",
  "reference" : "my-artifact",
  "version" : "master-h10.62bbbd6"
}
```


### Removing an environment pin via the API

To remove all pins from an environment, use:

`DELETE /managed/application/{application}/pin/{targetEnvironment}`


### Removing a specific pin via the API

You may want to remove a specific pin from an environment. To do that, you'll hit make a request like:

`DELETE /managed/application/{application}/pin`

with body:
```json

{
  "targetEnvironment": "test",
  "reference" : "my-artifact",
  "version" : "master-h10.62bbbd6"
}
```
