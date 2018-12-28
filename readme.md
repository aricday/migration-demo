# Migration Demo
This is a demonstration repository showing migration process for a sample folder and service.

## Sample using Gradle developer plugin and GMU
This example has been extended from the skeleton project found at [skeleton repo](https://github.com/ca-api-gateway-examples/gateway-developer-skeleton-repo.git) or this more [complex example](https://github.com/ca-api-gateway-examples/gateway-developer-example)

To initialize the *skeleton project* as a starting point for this demo, we altered:
`build.gradle`: On line [28](build.gradle) replace `<project-folder>` with the path of the folder where the sample service is located. It must start with a `/`

See more detail on using the gateway-developer-plugin here: [gateway-developer-plugin](https://github.com/ca-api-gateway/gateway-developer-plugin/wiki)

# Start this demo.
Put a valid gateway license in the `docker` folder. The license file should be called `license.xml`. For information on getting a license see the [License Section from the Gateway Container readme](https://hub.docker.com/r/caapim/gateway/).

## Running the Solution
In order to run the solution you need to do the following:

1) Put a valid gateway license in the `docker` folder. The license file should be called `license.xml`. For information on getting a license see the [License Section from the Gateway Container readme](https://hub.docker.com/r/caapim/gateway/).
2) Make sure you have already built the solution by running `./gradlew build`
3) Start the Gateway Container by running: `docker-compose up --force-recreate`

After the container is up and running you can connect the CA API Gateway Policy Manager to it.

## Exporting from your Gateway
If you connect to the running gateway with the CA API Gateway Policy Manager and make changes to the services and policies you can export those changes by running:

```./gradlew export```

This will export the changes to project folders. Note local edits will be overridden by changes from the gateway

## Building a Solution
In order to package the solution into something that can be applied to the CA API Gateway run the following Gradle command:

```./gradlew build```

## Stopping Docker container
To stop the running Gateway Container, run the following command:

`docker-compose down --volumes`


## License

Copyright (c) 2018 CA. All rights reserved.

This software may be modified and distributed under the terms
of the MIT license. See the [LICENSE][license-link] file for details.


 [license-link]: /LICENSE
 [contributing]: /CONTRIBUTING.md
