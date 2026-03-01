pipeline {
    agent any

    stages {
        stage('GIT') {
            steps {
                git branch: 'master',
                    changelog: false,
                    credentialsId: 'jenkins-github',
                    url: 'https://github.com/zeineb-ferchichi/student-management.git'
            }
        }

        stage('MAVEN Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Zeineb Ferchichi') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
