pipeline {
    agent {
        label 'windows'
    }

    stages {
        stage('Run only on develop or main') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'main'
                }
            }
            stages {
                stage('Checkout') {
                    steps {
                        checkout scm
                    }
                }

                stage('Restore Dependencies') {
                    steps {
                        bat 'dotnet restore'
                    }
                }

                stage('Build') {
                    steps {
                        bat 'dotnet build --no-restore'
                    }
                }

                stage('Test') {
                    steps {
                        bat 'dotnet test --no-build --verbosity normal'
                    }
                }
            }
        }
    }
}
