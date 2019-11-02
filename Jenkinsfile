pipeline {
  agent {
    docker {
      image 'maven:3-jdk-8'
    }

  }
  stages {
    stage('Clean') {
      agent any
      steps {
        sh 'mvn clean'
      }
    }
    stage('build') {
      steps {
        sh 'mvn install package'
      }
    }
    stage('test') {
      agent {
        docker {
          image 'mysql/mysql-server'
        }

      }
      steps {
        sh 'mvn test -B'
      }
    }
  }
  environment {
    MYSQL_DATABASE = 'db_fse_movie'
    MYSQL_CI_URL = 'jdbc:mysql://mysql/db_fse_movie'
    MYSQL_USER = 'fsemovieuser'
    MYSQL_PASSWORD = 'FsePassword'
    MYSQL_ROOT_PASSWORD = 'root'
  }
}