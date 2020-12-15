pipeline{

    agent any

    stages{
       stage("SCM Checkout"){
            steps{
                git 'https://github.com/sonaligaykhe/demo-project1.git'
                echo "************SCM Checkout Successful***********"
            }
        }
        stage("Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
                echo "************Build Successful***********"
            }
        }
        stage("Deploy"){
            steps{
                sshagent(['tomcat_deploy']) {
                    sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@13.127.126.153:/opt/apache-tomcat-8.5.61/webapps"
                    echo "************Deployment Successful***********"
                }
            }
        }
    }
}
