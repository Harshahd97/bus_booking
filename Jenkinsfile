pipeline {
    agent { label 'slave2' }
    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf Parcel-service'
                sh 'git clone https://github.com/Harshahd97/bus_booking.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
            }
        }
        stage('Run Locally') {
        steps {
                sh 'java -jar target/bus-booking-app-1.0-SNAPSHOT.jar &'
                sleep 30
            }
         }
        stage('Deploy') {
            steps {
                sh 'ssh root@172.31.28.191'
                sh 'scp /home/slave2/workspace/Bus_booking_project_develop/target/bus-booking-app-1.0-SNAPSHOT.jar root@172.31.28.191:/opt/apache-tomcat-8.5.98/webapps'
        }
        }
    } 
}
