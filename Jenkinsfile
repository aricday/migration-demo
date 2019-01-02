pipeline{
agent any
stages {
    stage('Checkout Code') {
        steps {
            checkout scm
        }
    }
    stage('Deploy New Bundle') {
        steps {
            sh '/var/lib/jenkins/workspace/MoveToDev/GMU_Artifacts/GatewayMigrationUtility.sh migrateIn -z /var/lib/jenkins/workspace/MoveToDev/GMU_Artifacts/sample_api_migrate/gw-1/argfiles/cloud.gateway.properties --bundle /var/lib/jenkins/workspace/MoveToDev/GMU_Artifacts/sample_api_migrate/gw-1/deploy/migration-demo-1.0.0.bundle --test'
        }
    }
   
}
}
