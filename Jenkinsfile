
pipeline {
agent{
label  any
}
stages{
stage ('build'){
steps {
 checkout scm 
sh 'sudo docker build -t react:${env.BRANCH_NAME} .'
sh 'sudo docker images'
}
}

stage('run'){
steps{
sh 'sudo docker run -d --name multi-doc react:${env.BRANCH_NAME}'
sh 'sudodocker ps -a'

}
}

stage('clean'){
steps{
sh 'sudo docker rm -f multi-doc'
sh 'sudo docker rmi react:${env.BRANCH_NAME}'
}
}
}
}
