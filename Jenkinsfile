pipeline {
    agent any

    stages {
        stage('GIT Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/LelutoDeku/Xebia-Webinar-3.git'
            }
        }

        stage('UNIT TESTING') {
            steps {
                sh 'mvn test'
            }
        }

        stage('INTEGRATION TESTING') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }

        stage('BUILD') {
            steps {
                sh 'mvn clean install'
            }
        }

        // stage('STATIC CODE ANALYSIS') {
        //     steps {
        //         script {
        //             withSonarQubeEnv(credentialsId: 'sonarqube1') {
        //                 sh 'mvn clean package sonar:sonar'
        //             }
        //         }
        //     }
        // }

        // stage('QUALITY GATE STATUS') {
        //     steps {
        //         script {
        //             waitForQualityGate abortPipeline: false, credentialsId: 'sonarqubetoken'
        //         }
        //     }
        // }

        stage('Upload Artifacts to Nexus'){
            
            steps{

                script{

                    nexusArtifactUploader artifacts: 
                    [
                        [
                            artifactId: 'springboot', 
                            classifier: '', 
                            file: 'target/UPES.jar', 
                            type: 'jar'
                        ]
                    ], 
                    credentialsId: 'hammad653', 
                    groupId: 'com.example', 
                    nexusUrl: '34.227.207.218:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'javacipipeline', 
                    version: '1.0.0'
            }
        }

    }
}

}