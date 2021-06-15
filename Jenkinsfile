pipeline {
    agent any

    stages {
        stage('export-integration') {
            steps {
                echo 'Export Integration..'
                build job: 'oic-export-integration', parameters: [
                    string(name: 'Integration_ID', value: "ECHO"),
                    string(name: 'Version', value: "01.02.0000"),
                    string(name: 'Environment', value: "Test"),
                    string(name: 'OCI_Repository', value: "oic-repository")
                ]
            }
        }
        stage('import-integration') {
            steps {
                echo 'Import Integration..'
            }
        }
    }
}
