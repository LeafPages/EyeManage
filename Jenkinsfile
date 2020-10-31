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
      }
    }

  }
}