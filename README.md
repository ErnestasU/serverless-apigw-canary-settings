###

This is the extension of `serverless.com` framework which let's to create canary deployment for API Gateway.

#### Usage

Add custom settings for canary in `serverless.yml` file:

```
custom:
  apiGatewayDeployment:
    canary:
      trafficInPercentages: 0
```

then invoke `serverless deploy --canaryDeployment true` to deploy API Gateway to canary deployment