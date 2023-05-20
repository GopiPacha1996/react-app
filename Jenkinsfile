
def Agent = null
node ('master'){
stage('CheckoutSCM and set Node'){
checkout scm 
if (env.BRANCH_NAME == 'master') {
Agent = 'prod'
}
if (env.BRANCH_NAME == 'develop'){
Agent = 'dev'
}
else (env.BRANCH_NAME = 'qa'){
Agent = 'dev'
}
}
}

pipeline {
 agent {
 label '$Agent'
 }
stages{
stage ('build'){
steps {
 checkout scm 
sh """
echo "this is build stage"
"""
 
}
}

stage('run'){
steps{
sh """
echo "this is Run stage"
"""

}
}

stage('clean'){
steps{
sh """
echo "this is clean stage"
"""
}
}
}
}
