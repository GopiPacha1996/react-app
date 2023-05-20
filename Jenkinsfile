pipeline {
 agent {
 label 'prod'
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
