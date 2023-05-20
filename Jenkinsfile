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
sudo docker build -t test:v1 .
"""
 
}
}

stage('deploy_qa'){
  when { branch 'qa' 
        
       }
       agent { 
        label 'dev' 
       }
steps{
sh """
echo "this is qa_deploy"
"""

}
}

stage('deploy_prod'){
 when { branch 'master' 
        }
       agent { 
        label 'prod' 
       }
steps{
sh """
echo "this is prod_deploy"
"""
}
}
}
}
