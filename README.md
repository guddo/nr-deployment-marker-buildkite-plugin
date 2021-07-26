# New Relic Deployment Marker Buildkite Plugin
Buildkite Plugin that publishes a New Relic Deployment Marker

Deployment markers on you application deployments allow for quick troubleshooting in New Relic post a deployment.

Runs the New Relic Deployment Marker post command described 
[here](https://docs.newrelic.com/docs/apm/new-relic-apm/maintenance/record-monitor-deployments/#post-deployment)

## Example

Add the following to your `pipeline.yml`:

```
steps:
- env:
  name: ":rocket: deploy my funky app"
  command:
  - <some deployment command>
  plugins:
  - ssh://git@github.com/AfterpayTouch/platform-nr-deployment-marker-buildkite-plugin.git#v1.0.0:
      nr_app_id: '<new relic app id>'
```

## Configuration

### `nr_app_id` (Required, string)

New Relic App ID. You can find your Application's New Relic App ID by following instructions mentioned 
[here](https://docs.newrelic.com/docs/apis/rest-api-v2/get-started/get-app-other-ids-new-relic-one/#ui)

## Other Configuration

The plugin expects the following to be present as these details are used as information for the deployment marker.

+ `APP_VERSION` environment variable or `application_version` buildkite meta-data key
+ `BUILDKITE_PIPELINE_NAME` environment variable
+ `BUILDKITE_BUILD_NUMBER` environment variable
+ `BUILDKITE_BUILD_URL` environment variable
+ `BUILDKITE_BUILD_CREATOR_EMAIL` environment variable

## Developing

To run the tests:

```shell
docker-compose run --rm tests
```

## Contributing

1. Fork the repo
2. Make the changes
3. Run the tests
4. Commit and push your changes
5. Send a pull request
