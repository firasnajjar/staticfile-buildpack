# Cloud Foundry Staticfile Buildpack

[![CF Slack](https://www.google.com/s2/favicons?domain=www.slack.com) Join us on Slack](https://cloudfoundry.slack.com/messages/buildpacks/)

A Cloud Foundry [buildpack](http://docs.cloudfoundry.org/buildpacks/) for static content such as websites (HTML/JS/CSS).

### Buildpack User Documentation

Official buildpack documentation can be found at [staticfile buildpack docs](http://docs.cloudfoundry.org/buildpacks/staticfile/index.html).

### Building the Buildpack

1. Install buildpack-packager

    ```shell
    (cd src/staticfile/vendor/github.com/cloudfoundry/libbuildpack/packager/buildpack-packager && go install)
    ```

1. Build the buildpack

    ```shell
    buildpack-packager [ --cached | --uncached ]
    ```

1. Use in Cloud Foundry

  Upload the buildpack to your Cloud Foundry and optionally specify it by name

    ```bash
    cf create-buildpack [BUILDPACK_NAME] [BUILDPACK_ZIP_FILE_PATH] 1
    cf push my_app -b [BUILDPACK_NAME]
    ```

### Testing
Buildpacks use the [Cutlass](https://github.com/cloudfoundry/libbuildpack/cutlass) framework for running integration tests.

To test this buildpack, run the following command from the buildpack's directory:

1. Install ginkgo

    ```bash
    (cd src/staticfile/vendor/github.com/onsi/ginkgo/ginkgo && go install)
    ```

1. Run unit tests

    ```bash
    ./scripts/unit.sh
    ```

1. Run integration tests

    ```bash
    ./scripts/integration.sh
    ```

More information can be found on github [cutlass](https://github.com/cloudfoundry/libbuildpack/cutlass).

### Contributing

Find our guidelines [here](./CONTRIBUTING.md).

### Help and Support

Join the #buildpacks channel in our [Slack community](http://slack.cloudfoundry.org/) if you need any further assistance.

### Reporting Issues

Open a GitHub issue on this project [here](https://github.com/cloudfoundry/staticfile/issues/new)

### Active Development

The project backlog is on [Pivotal Tracker](https://www.pivotaltracker.com/projects/1042066)

### Acknowledgements

This buildpack is based heavily upon Jordon Bedwell's Heroku buildpack and the modifications by David Laing for Cloud Foundry [nginx-buildpack](https://github.com/cloudfoundry-community/nginx-buildpack). It has been tuned for usability (configurable with `Staticfile`) and to be included as a default buildpack (detects `Staticfile` rather than the presence of an `index.html`). Thanks for the buildpack Jordon!
