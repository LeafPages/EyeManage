pipeline {
  agent any
  stages {
    stage('Dev Build') {
      steps {
        git(url: 'https://github.com/LeafPages/EyeManage', branch: 'master', changelog: true)
        bat(script: 'mvn install', label: 'Maven Dev Build')
      }
    }

    stage('Smoke Tests') {
      steps {
        git(url: 'https://github.com/LeafPages/EyeAutomation', branch: 'master')
        bat(script: 'mvn test -DEnvironment=Dev', label: 'Smoke tests')
      }
    }

    stage('QA Build (AWS)') {
      steps {
        echo 'Build to be moved to QA Environment using SSH'
      }
    }

    stage('Integration Test') {
      steps {
        bat 'mvn test -DEnvironment=QA'
      }
    }

  }
}