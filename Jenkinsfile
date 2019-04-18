pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/maven_361/bin/mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh '/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/maven_361/bin/mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
