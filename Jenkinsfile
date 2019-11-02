pipeline {
  agent {
    docker {
      image 'mysql/mysql-server'
    }

  }
  stages {
    stage('Clean') {
      agent {
        docker {
          image 'mysql'
        }

      }
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