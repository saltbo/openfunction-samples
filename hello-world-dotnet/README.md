# Sample Function Dotnet

## Run on OpenFunction

1. [Install OpenFunction](https://github.com/OpenFunction/OpenFunction#quickstart)
2. [Run a function](https://github.com/OpenFunction/OpenFunction#sample-run-a-function)

Definition of a ```Function``` for ```dotnet``` is shown below:

> When having poor network connectivity to GitHub/Googleapis:
>
> Change ```gcr.io/buildpacks/builder``` to ```openfunction/buildpacks-builder:v1```

```yaml
apiVersion: core.openfunction.io/v1alpha1
kind: Function
metadata:
  name: dotnet-sample
spec:
  funcName: "helloworld"
  funcType: "http"
  funcVersion: "v1.0.0"
  builder: "gcr.io/buildpacks/builder:v1"
  source:
    url: "https://github.com/OpenFunction/function-samples.git"
    sourceSubPath: "hello-world-dotnet"
  image: "<your registry name>/sample-dotnet-func:latest"
  registry:
    url: "https://index.docker.io/v1/"
    account:
      name: "basic-user-pass"
      key: "username"
  runtime: "Knative"
  port: 8080
```