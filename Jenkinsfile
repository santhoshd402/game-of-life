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
}
