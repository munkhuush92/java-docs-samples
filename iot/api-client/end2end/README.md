# Google Cloud IoT Core Java Samples

<a href="https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/java-docs-samples&page=editor&open_in_editor=iot/api-client/manager/README.md">
<img alt="Open in Cloud Shell" src ="http://gstatic.com/cloudssh/images/open-btn.png"></a>

This directory contains samples for Google Cloud IoT Core. [Google Cloud IoT Core](https://cloud.google.com/iot/docs/ "Google Cloud IoT Core") allows developers to easily integrate Publish and Subscribe functionaliy with devices and progmatically manage device authorization.

Note that before you can run the sample, you must configure a Google Cloud
PubSub topic for Cloud IoT as described in [the parent README](../README.md).

Before running the samples, you can set the `GOOGLE_CLOUD_PROJECT` and
`GOOGLE_APPLICATION_CREDENTIALS` environment variables to avoid passing them to
the sample every time you run it.

## Setup

### Authentication

This sample requires you to have authentication setup. Refer to the [Authentication Getting Started Guide](https://cloud.google.com/docs/authentication/getting-started "Google Cloud IoT Core") for instructions on setting up credentials for applications.

Run the following command to install the libraries and build the sample with Maven:

    mvn clean compile assembly:single

## Samples

### Server

<a href="https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/java-docs-samples&page=editor&open_in_editor=iot/api-client/manager/README.md">
<img alt="Open in Cloud Shell" src ="http://gstatic.com/cloudssh/images/open-btn.png"></a>

To run this sample:

    mvn exec:java \
        -Dexec.mainClass="com.example.cloud.iot.endtoend.CloudiotPubsubExampleServer" \
        -Dexec.args="-project_id=<your-iot-project> \
                    -pubsub_subscription=<your-pubsub-subscription>"

### Device

<a href="https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/java-docs-samples&page=editor&open_in_editor=iot/api-client/manager/README.md">
<img alt="Open in Cloud Shell" src ="http://gstatic.com/cloudssh/images/open-btn.png"></a>

To run this sample:

    mvn exec:java \
      -Dexec.mainClass="com.example.cloud.iot.endtoend.CloudiotPubsubExampleMqttDevice" \
      -Dexec.args="-project_id=<your-iot-project> \
                   -registry_id=<your-registry-id> \
                   -device_id=<device-id> \
                   -private_key_file=<path-to-keyfile> \
                   -algorithm=<RS256|ES256>"

For example, if your project ID is `blue-jet-123`, your device registry id is
`my-registry`, your device id is `my-device` and you have generated your
credentials using the [`generate_keys.sh`](../generate_keys.sh) script
provided in the parent folder, you can run the sample as:

    mvn exec:java \
        -Dexec.mainClass="com.example.cloud.iot.endtoend.CloudiotPubsubExampleMqttDevice" \
        -Dexec.args="-project_id=blue-jet-123 \
                     -registry_id=my-registry \
                     -device_id=my-device \
                     -private_key_file=../rsa_private_pkcs8 \
                     -algorithm=RS256"
