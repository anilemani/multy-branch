pipeline {
     agent any
     
    stages {
        stage('clone-repo') {
            steps {
                git 'https://github.com/nageshvkn/gamutkart2.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
         stage('test-case') {
            steps {
                sh 'mvn install'
            }
        }  
         stage('deployment') {
            steps {
                sh 'sshpass -p "mohith" scp target/gamutgurus.war mohith@172.17.0.4:/home/mohith/apache-tomcat-9.0.59/webapps'
                sh 'sshpass -p "mohith" ssh mohith@172.17.0.4 /home/mohith/apache-tomcat-9.0.59/bin/startup.sh'
            }
        }
    }
}

