pipeline {
    agent any
    stages { 
        stage('Setup') {
            steps {
                script {
                    startZap(host: localhost, port: 5555, timeout:500, zapHome: ".ZAP",  allowedHosts:['https://akilaliyanage.github.io']) // Start ZAP at /opt/zaproxy/zap.sh, allowing scans on github.com
                }
            }
        }
    post {
        always {
            script {
                archiveZap(failAllAlerts: 1, failHighAlerts: 0, failMediumAlerts: 0, failLowAlerts: 0, falsePositivesFilePath: "zapFalsePositives.json")
            }
        }
    }
}
