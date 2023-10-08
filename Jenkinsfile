pipeline{
    agent any
    environment{
        staging_server="127.0.0.1"
    }
    stages{
        stage('Deploy to Local'){
            steps{
                sh '''
                    for fileName in `find ${WORKSPACE} -type f -mmin -10 | grep -v ".git" | grep -v "Jenkinsfile"`
                    do
                        fil=$(echo ${fileName} | sed 's/'"${JOB_NAME}"'/ /' | awk {'print $2'})
                        sudo scp -r ${WORKSPACE}${fil} /var/www/html/mydomain${fil}
                    done
                '''
            }
        }
    }
}
