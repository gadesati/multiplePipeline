pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_6_3') {
                    sh 'mvn clean install'
                }
            }
        }

    /*    stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_6_3'') {
                    sh 'mvn test'
                }
            }
        }
*/

        stage ('Deployment Stage') {
            steps {
                echo "deploying to tomcat "
                deploy adapters: [tomcat9(credentialsId: 'be75ce54-d908-48fe-8ae8-eebf2dd97fa6', path: '', url: 'http://15.206.166.170:8090/')], contextPath: 'sample', war: '**/*war'
               /* sh '/usr/local/bin/aws s3 cp target/jenkins-example*.jar s3://techprimers-s3/'
                sh '/usr/local/bin/aws s3 ls'
                sh '/usr/local/bin/aws s3 ls s3://techprimers-s3/' */
            }
        }
    }
}
