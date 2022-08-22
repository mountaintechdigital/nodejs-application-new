node{
    def mavenHome = tool name: 'maven3.6.3'

    stage('SCM Clone'){
      git credentialsId: 'GitHubCredentials', url: 'https://github.com/mountaintechdigital/nodejs-application.git'
    }

    stage('NodeJS Build'){
      //sh '${mavenHome}/bin/mvn clean package'
    }

    stage('Quality Report'){
      //sh '${mavenHome}/bin/mvn sonar:sonar'
    }

    stage('Artifactory Upload'){
      //sh '${mavenHome}/bin/mvn deploy'
    }


    stage('Docker Build'){
      sh 'docker build -t mountaintechdigital/nodejs-application .'
    }

    stage('Docker Push'){
      withCredentials([string(credentialsId: 'DockerHubCredentials', variable: 'DockerHubCredentials')]){
        sh 'docker login -u mountaintechdigital -p ${DockerHubCredentials}'
      }
      sh 'docker push mountaintechdigital/nodejs-application'

    }

    stage('Remove Docker Images'){
    //   sh 'docker rmi -f $(docker images -q)'
    }

    stage('Deploy to K8s'){
    //   sh 'kubectl apply -f app.yml'
    }


  }
