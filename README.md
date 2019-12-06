###

This is the plugin of `Serverless` framework which let's to create canary deployment for API Gateway.

This addresses two things:

1. Canary deployments for API Gateway
2. Concrete lambda function version binding to API Gateway (instead of $LATEST, it will take current deployed lambda version)

Second point above enables API Gateway canary deployments since it binds concrete lambda version to concrete API Gateway deployment.
It allows _base version_ to point to concrete deployment, whilst canary can point to not yet promoted version. Using this principle,
Blue/Green deployment can be achieved, meaning that canary can take either 100% or 0% traffic if needed. 


#### Installation

Run `npm install --save-dev serverless-apigw-canary-settings`, and add this plugin to `serverless.yml`. It will hook to package phase, meaning either `package` or `deploy` phases will trigger this plugin if used as specified below. 

#### Usage

Add custom settings for canary in `serverless.yml` file:

```
custom:
  apiGatewayDeployment:
    canary:
      trafficInPercentages: 0
```

then invoke `serverless deploy --canaryDeployment true` to deploy API Gateway to canary deployment.

Custom option `--canaryDeployment` requires `true/false` value in order to allow enable canary deployments for API Gateway.
If value is `true`, then `custom.apiGatewayDeployment` settings are read from `serverless.yml` file and applied for canary deployment.
Otherwise, no action is taken.
