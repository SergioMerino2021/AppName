node {
    def myGradleContainer = docker.image('gradle:jdk8-alpine')
    myGradleContainer.pull()

    stage('Preparación') {
        git branch: 'main', url: 'https://github.com/SergioMerino2021/AppName.git'
    }


    stage('Sonar Scanner') {
      def sonarqubeScannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      withCredentials([string(credentialsId: 'sonar', variable: 'sonarLogin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://192.168.1.204:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=gs-gradle -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=GS -Dsonar.sources=complete/src/main/ -Dsonar.tests=complete/src/test/ -Dsonar.language=java -Dsonar.java.binaries=."
      }
    }
}
