# aws-lambda-net-insights-runtime
Small repo to demo the Lambda Insights reporting a Custom runtime for .NET 3.1 runtime


## Issue
Lambda Insights provides a report of various metrics for a Lambda invocation. Part of this includes the Runtime that a function was invoked under. When running a .NET Core 3.2 Runtime, the expected output for the Insights Runtime property is `.NET3.1`, instead of `Custom`.

## Reproduction
Clone this repo
`cd customRuntimeBug`
`npm install`
Build
`npm run buildwin` or `npm build osx`
`npm run deploy`
`npm run invoke`

### Expected output
This will create a log in the Cloudwatch Logs namespace `/aws/lambda-insights` prefixed with `customruntimebug-dev-hello`. This will contain a debug object with the following property:
`"runtime"`.

It would be expected that this value contains `.NET3.1`

### Actual output
An object with the property
`"runtime": "Custom",`