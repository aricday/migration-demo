
# K8S MIGRATION

## Service & Policy migration commands

### Browse IDs - Source:
` ./GatewayMigrationUtility.sh browse -z gm_gmu/argfiles/k8s.gateway.properties -r --showIds `

### Migrate In - Source:
` ./GatewayMigrationUtility.sh migrateIn -z gm_gmu/argfiles/k8s.gateway.properties --template gm_gmu/templates/gm_base_local_vars.properties --bundle gm_gmu/bundles/gm_base_bundle.bundle  --map gm_gmu/mappings/gm_base_local.mappings.xml --test `

### Migrate Out - Local Source:
` ./GatewayMigrationUtility.sh migrateOut -z gm_gmu/argfiles/k8s.gateway.properties --all -d gm_gmu/bundles/gm_base_config.orig.xml --defaultAction NewOrUpdate `

### Externalize the variables with the values from the exported policy xml using the TEMPLATE command
` ./GatewayMigrationUtility.sh template --bundle gm_gmu/bundles/gm_base_bundle.bundle --template gm_gmu/templates/gm_base_gcp1_vars.properties `

### Manage Mappings (if any):
` ./GatewayMigrationUtility.sh manageMappings --bundle gm_gmu/bundles/gm_base_bundle.bundle --type LOG_SINK, AUDIT_CONFIG, FIREWALL_RULE | SSG_KEY_ENTRY --action IGNORE | NewOrExisting --outputFile gm_gmu/mappings/gm_base_gw1.mappings.xml `

### Migrate In - GW1 Target:
` ./GatewayMigrationUtility.sh migrateIn -z gm_gmu/argfiles/gw1.gateway.properties --template gm_gmu/templates/gm_base_gcp1_vars.properties --bundle gm_gmu/bundles/gm_base_bundle.bundle  --map gm_gmu/mappings/gm_base_gw1.mappings.xml --test `

### Migrate In - gw-svc Target:
` ./GatewayMigrationUtility.sh migrateIn -z gm_gmu/argfiles/gw-svc.gateway.properties --template gm_gmu/templates/gm_base_gcp1_vars.properties --bundle gm_gmu/bundles/gm_base_bundle.bundle  --map gm_gmu/mappings/gm_base_gw1.mappings.xml --test `

### ServiceEdit - gw-svc Target:
` ./GatewayMigrationUtility.sh migrateIn -z gm_gmu/argfiles/gw-svc.gateway.properties --bundle gm_gmu/bundles/edit_virus.bundle --test `

### BIG_BUNDLE - gw-svc (needs to remove prev IdP/Policy)
` ./GatewayMigrationUtility.sh migrateIn -z gm_gmu/argfiles/k8s.gateway.properties --bundle gm_gmu/bundles/intra_preprod.bundle `

