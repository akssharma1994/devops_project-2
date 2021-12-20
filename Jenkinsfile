pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/akssharma1994/devops_project-2.git'
            }
        }
        stage('approval'){
            steps {
                input message: '"validating user"', submitter: 'dev'
            }
        }
        stage('validating user'){
            steps{
                script {
                    if (env.CHANGE_AUTHOR == 'QA_USER') {
                        echo 'I only execute on the master branch'
                        } 
                    else {
                        echo 'I execute elsewhere'
                    }
                }    
            }
        }        
        stage ('build'){
            steps{
                echo "This is a build stage"
                sh 'mvn clean package'
            }
        }    
    }    
}
