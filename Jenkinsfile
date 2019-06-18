node {
    def mvnHome
    stage('Cloning Git') {
        git 'https://github.com/koushik94949/CI-with-Jenkins-in-AWS-Demo.git'
		mvnHome = tool 'mymaven'
      }
    stage('Compile') {
         sh 'mvn compile'
       }
    stage('Test') {
        sh 'mvn test'
		junit '**/target/surefire-reports/TEST-*.xml'
      }
	stage('Review') {
        sh 'mvn pmd:pmd'
      }
	stage('Package') {
        sh 'mvn package'
      }
	stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'project/target/*.war'
 
    }
 }
