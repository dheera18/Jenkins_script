pipeline {
    agent { label "Slave1" }

      triggers {
        pollSCM('* * * * *')
    }   

    stages {
        stage('Stage1_clone') {
            steps {
                echo 'clone my project'
                git branch: 'main', url: 'https://github.com/dheera18/Helloworld_latest.git'     
                }
        }
          stage('Stage2_Build') {
            steps {
                echo 'Build my project'
                sh 'yum install maven -y'
                sh 'mvn -Dmaven.test.failure.ignore=true install'
                
            }
        }
          stage('Stage3_Deploy') {
            steps {
                echo 'Deploy my project'
                deploy adapters: [tomcat8(credentialsId: 'tomcat_admin', path: '', url: 'http://http://3.84.242.224/')], contextPath: null, war: '**/*.war'
            }
        }
        stage('Stage4_Test1') {
            steps {
                echo 'Test my project'
            }
        }
           stage('Stage5_Test2') {
            steps {
                echo 'Test my project again'
            }
        }
    }
}
