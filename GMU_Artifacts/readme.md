# GMU Command Samples 
This is a demonstration script showing migration process for a sample folder and service.

## To browse environment artifacts:

`./GatewayMigrationUtility.sh browse -z sample_api_migrate/gw-1/argfiles/cloud.gateway.properties -r --showIds`

## Migrate In the "base" dev bundle from workstation: (--test)

`./GatewayMigrationUtility.sh migrateIn -z sample_api_migrate/gw-1/argfiles/cloud.gateway.properties --bundle sample_api_migrate/gw-1/deploy/migration-demo-1.0.0.bundle --test`

## Migrate Out policy changes for QA server & export to source code repo.
If you connect to the running gateway with the CA API Gateway Policy Manager and make changes to the services and policies you can export those changes by running:

`./GatewayMigrationUtility.sh migrateOut -z sample_api_migrate/gw-1/argfiles/cloud.gateway.properties --dest sample_api_migrate/gw-1/bundles/gw1.out.migration-demo.xml --folderName /migration-demo`

This will export any changes to the sample migration bundle. 

## Externalize the variables with the values from the exported policy xml using the TEMPLATE command
In order to package the environment variables into property templates that can be applied to the CA API Gateway environments

`./GatewayMigrationUtility.sh template --bundle sample_api_migrate/gw-1/bundles/gw1.out.migration-demo.xml --template sample_api_migrate/gw-1/templates/gw1.migration-demo.properties`
   - *NOTE: This will create the template environment properties file with the key / value pair having variable names and corresponding values, and the values in the file can be modified with specific environment properties.*

## Manage Mappings:
In order to manage the dependency mappings, create a mappings output file for target:

`./GatewayMigrationUtility.sh manageMappings --bundle sample_api_migrate/gw-1/bundles/gw1.out.migration-demo.xml --type SSG_KEY_ENTRY --action IGNORE  --outputFile sample_api_migrate/gw-1/mappings/gw1.gw2.migration-demo.mappings.xml`

`./GatewayMigrationUtility.sh manageMappings --bundle sample_api_migrate/gw-1/bundles/gw1.out.migration-demo.xml --type CLUSTER_PROPERTY --action NewOrExisting  --outputFile sample_api_migrate/gw-1/mappings/gw1.gw2.migration-demo.mappings.xml`

## Migrate In to the new environment: (--test)

`./GatewayMigrationUtility.sh migrateIn -z sample_api_migrate/gw-2/argfiles/mag.gateway.properties --template sample_api_migrate/gw-1/templates/gw1.sample-folder.properties --bundle sample_api_migrate/gw-1/bundles/gw1.out.sample-folder.xml  --map sample_api_migrate/gw-1/mappings/gw1.gw2.sample-folder.mappings.xml --test`

