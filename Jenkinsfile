pipeline {
  agent any
  stages {
    stage('Pre Build') {
      parallel {
        stage('Pre Build') {
          steps {
            sh '''java -version
mvn --version
git --version'''
          }
        }

        stage('Log Versions') {
          steps {
            fileExists 'pom.xml'
          }
        }

      }
    }

    stage('Build with Maven') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('Write Status') {
      steps {
        writeFile(file: 'status.txt', text: 'It worked!')
      }
    }

  }
}