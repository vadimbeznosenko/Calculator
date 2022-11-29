pipeline {
    agent none

options { disableConcurrentBuilds() }
    stages {
        stage ('Build on Windows'){
            agent {label 'agent_win'}
            steps {

            withMaven(
            jdk: 'openlogic-openjdk-8u352-b08-windows',
            maven: 'apache-maven-3.5.0-win'){
            bat "mvn package"
            configFileProvider([configFile(fileId: '74cbfc27-4f65-4b19-bb16-f2eb44d36b2c',
            targetLocation: 'C:/jenkins/workspace/test_maven_dev/settings',
            variable: 'MAVEN_SETTINGS')])  {
                bat "mvn -s $MAVEN_SETTINGS deploy"

                }
            }
            }
        post {
        always {
            cleanWs()
        }
        }
        }
       stage ('Build on Linux') {
            agent {label 'agent_lin'}
            steps {
            withMaven(
            jdk: 'java/jdk-8u202-linux',
            maven: 'apache-maven-3.5.0-lin')
{
            configFileProvider([configFile(fileId: '74cbfc27-4f65-4b19-bb16-f2eb44d36b2c',
            targetLocation: 'C:/jenkins/workspace/test_maven_dev/settings',
            variable: 'MAVEN_SETTINGS')])  {

                sh 'mvn -s $MAVEN_SETTINGS deploy'

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
