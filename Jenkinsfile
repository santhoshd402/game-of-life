node('maven') {
    stage('clone') {
    git 'https://github.com/santhoshd402/game-of-life.git'
}
    stage('build') {
    sh 'mvn clean package'
}
    stage('outputs') {
    junit 'gameoflife-web/target/surefire-reports/*.xml'
    archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
}
    stage('shareartifact') {
    sh "curl -u admin:Santhu@d402 -T /home/jenkins/test/workspace/proj-jfrog/gameoflife-web/target/*.war http://100.25.43.47:8082/artifactory/gameoflife/gameoflife${BUILD_NUMBER}.war"

}
    stage('SonarQube analysis') {
    // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
    withSonarQubeEnv('SONAR-6.7.4') {
      // requires SonarQube Scanner for Maven 3.2+
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
    }
    }

}
