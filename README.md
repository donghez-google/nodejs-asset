[//]: # "This README.md file is auto-generated, all changes to this file will be lost."
[//]: # "To regenerate it, use `npm run generate-scaffolding`."
<img src="https://avatars2.githubusercontent.com/u/2810941?v=3&s=96" alt="Google Cloud Platform logo" title="Google Cloud Platform" align="right" height="96" width="96"/>

# [Google Cloud Asset Inventory: Node.js Client](https://github.com/googleapis/nodejs-asset)

[![release level](https://img.shields.io/badge/release%20level-alpha-orange.svg?style&#x3D;flat)](https://cloud.google.com/terms/launch-stages)
[![npm version](https://img.shields.io/npm/v/@google-cloud/asset.svg)](https://www.npmjs.org/package/@google-cloud/asset)
[![codecov](https://img.shields.io/codecov/c/github/googleapis/nodejs-asset/master.svg?style=flat)](https://codecov.io/gh/googleapis/nodejs-asset)

[Cloud Asset Inventory](https://cloud.google.com/resource-manager/docs/cloud-asset-inventory/overview) is a storage service that keeps a five week history of Google Cloud Platform (GCP) asset metadata. It allows you to export all asset metadata at a certain timestamp or timeframe.


* [Using the client library](#using-the-client-library)
* [Versioning](#versioning)
* [Contributing](#contributing)
* [License](#license)

## Using the client library

1.  [Select or create a Cloud Platform project][projects].

1.  [Enable billing for your project][billing].

1.  [Enable the Google Cloud Asset Inventory API][enable_api].

1.  [Set up authentication with a service account][auth] so you can access the
    API from your local workstation.

1. Install the client library:

        npm install --save @google-cloud/asset

1. Try an example:

```javascript
  const asset = require('@google-cloud/asset');
  const client = new asset.v1beta1.AssetServiceClient({
    // optional auth parameters.
  });

  // Your Google Cloud Platform project ID
  const projectId = await client.getProjectId();
  console.log(projectId);
  const projectResource = client.projectPath(projectId);

  // var dumpFilePath = 'Dump file path, e.g.: gs://<my_bucket>/<my_asset_file>'
  const outputConfig = {
    gcsDestination: {
      uri: dumpFilePath,
    },
  };
  const request = {
    parent: projectResource,
    outputConfig: outputConfig,
  };

  // Handle the operation using the promise pattern.
  const [operation] = await client.exportAssets(request);
  // Operation#promise starts polling for the completion of the operation.
  const [result] = await operation.promise();
  // Do things with with the response.
  console.log(result);
```


The [Cloud Asset Node.js Client API Reference][client-docs] documentation
also contains samples.

## Versioning

This library follows [Semantic Versioning](http://semver.org/).

This library is considered to be in **alpha**. This means it is still a
work-in-progress and under active development. Any release is subject to
backwards-incompatible changes at any time.

More Information: [Google Cloud Platform Launch Stages][launch_stages]

[launch_stages]: https://cloud.google.com/terms/launch-stages

## Contributing

Contributions welcome! See the [Contributing Guide](https://github.com/googleapis/nodejs-asset/blob/master/.github/CONTRIBUTING.md).

## License

Apache Version 2.0

See [LICENSE](https://github.com/googleapis/nodejs-asset/blob/master/LICENSE)

## What's Next

* [Cloud Asset Documentation][product-docs]
* [Cloud Asset Node.js Client API Reference][client-docs]
* [github.com/googleapis/nodejs-asset](https://github.com/googleapis/nodejs-asset)

Read more about the client libraries for Cloud APIs, including the older
Google APIs Client Libraries, in [Client Libraries Explained][explained].

[explained]: https://cloud.google.com/apis/docs/client-libraries-explained

[client-docs]: https://cloud.google.com/nodejs/docs/reference/asset/latest/
[product-docs]: https://cloud.google.com/resource-manager/docs/cloud-asset-inventory/overview
[shell_img]: https://gstatic.com/cloudssh/images/open-btn.png
[projects]: https://console.cloud.google.com/project
[billing]: https://support.google.com/cloud/answer/6293499#enable-billing
[enable_api]: https://console.cloud.google.com/flows/enableapi?apiid=cloudasset.googleapis.com
[auth]: https://cloud.google.com/docs/authentication/getting-started
