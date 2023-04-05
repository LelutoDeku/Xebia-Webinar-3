pipeline {

    agent any

    stages {
        stage('GIT Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vishalchauhan91196/javacicode.git'
            }

        }
        stage ('UNIT TESTING')  {
            steps (
                sh 'mvn test'
            )
        }
        // stage ('INTEGRATION TESTING')   {
        //     steps(
        //         sh 'mvn verify -DskipUnitTests'
        //     )
        // }
    }
}