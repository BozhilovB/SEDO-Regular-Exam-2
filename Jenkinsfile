pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/BozhilovB/SEDO-Regular-Exam-2.git'
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore Horizons.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build Horizons.sln --configuration Release'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test Horizons.Tests.Unit/Horizons.Tests.Unit.csproj --no-build --configuration Release --verbosity normal'
            }
        }
    }
}
