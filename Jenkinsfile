node {
   
   stage('Preparation') { // for display purposes
    git 'https://github.com/RiteshDevOpsTrainer/april2020.git'
   }
   
   stage('Build') {
      def mvnHome
	  mvnHome = tool 'MVN_HOME'
      withEnv(["MVN_HOME=$mvnHome"]) {
        sh '$MVN_HOME/bin/mvn clean install package'
      }
   }
   
   stage('deploy') {
     deploy adapters: [tomcat9(credentialsId: 'af31b8ed-94a3-4585-aaad-9c78c35abf34', path: '', url: 'http://192.168.1.104:9080')], contextPath: null, onFailure: false, war: '**/*war'
   }
   
   stage('Notification'){
     emailext attachLog: true, body: '''Dear Team,<br>Your project has been executed successfully. ''', subject: 'DevOps Pipeline Execution', to: 'ritesh.goyal590@gmail.com'
   }
}
