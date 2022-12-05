pipeline {
    agent none

options { disableConcurrentBuilds() }
    stages {
       stage ('Build on Linux') {
            agent {label 'agent_lin'}
            steps {
            withMaven(
            jdk: 'java/jdk-8u202-linux',
            maven: 'apache-maven-3.5.0-lin')
{
            configFileProvider([configFile(fileId: '74cbfc27-4f65-4b19-bb16-f2eb44d36b2c',
            targetLocation: "${WORKSPACE}/settings",
            variable: 'MAVEN_SETTINGS')])  {
                
                sh "mvn clean"
                sh "mvn -s $MAVEN_SETTINGS deploy"

}
            }
        }
                post {
        always {
            cleanWs()
        }
        }
       }
    }
}
