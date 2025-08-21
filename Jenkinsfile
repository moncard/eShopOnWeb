pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Test/Shell Script') {
      parallel {
        stage('Test / Shell Script') {
          steps {
            sh 'dotnet test tests/UnitsTests'
          }
        }

        stage('Integration / Shell Script') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment / Shell Script') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet '
      }
    }

  }
}