def Agent = null
node ('master'){
stage('CheckoutSCM and set Node'){
checkout scm 
if (env.BRANCH_NAME == 'master') {
Agent = 'console'
}
if (env.BRANCH_NAME == 'develop'){
Agent = 'datanow'
}
else (env.BRANCH_NAME = 'qa'){
Agent = 'qa-lightsail'
}
}

pipeline {
agent{
lable  Agent
}
stage ('scm'){
checkout scm

}
stage ('build'){
steps {
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
sh 'sudo docker rmi react:${env.BRANCH_NAME}
}
}

}
