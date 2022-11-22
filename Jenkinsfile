node {

    stage('Preparación') {
        git branch: 'main', url: 'https://github.com/SergioMerino2021/AppName.git'
    }


    stage("Sonar Scan") {
          withEnv(["PATH=/usr/bin:/usr/local/jdk-11.0.2/bin:/opt/sonarqube/sonar-scanner/bin/"]) {
            withSonarQubeEnv(installationName: 'http://192.168.1.204:9000', credentialsId: 'sonar') {  
            sh "sonar-scanner \
                -Dsonar.projectKey=test \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://192.168.1.204:9000 \
                -Dsonar.login=331ddd378d3b306355dfd282179b4cfa68249298"
         }
      }
    }

}
