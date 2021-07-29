
node {
    def mvnHome = tool 'Maven'
    registryName = "MyNewConReg"
    registryUrl = "mynewconreg.azurecr.io"
    registryCredential= "MyNewConReg"
    
    
    stage('checkout'){
        echo "Into Checkout"
        //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sujana-Suresh/myPythonDockerRepo.git']]])
         checkout scm
          }
    
    stage('Build'){
        echo "Into Build"
        sh "${mvnHome}/bin/mvn clean install -f pom.xml"
          }
    
    stage ('Build Docker image'){
        echo "Into buiding docker image"
        docker.build registryName
          }
          
    stage('ACR Push') {
        sh "az acr login -n myakacrregistry --username myakacrregistry --password tlQv=XzxYOf/Ix8+tZj/Uj3lFelycVjG"
        sh " docker tag testimage myakacrregistry.azurecr.io/testimage:latest"
        sh " docker push myakacrregistry.azurecr.io/testimage:latest"
         }
 
  //  stage('AKS deploy'){
     //   sh 'az aks install-cli'
        //sh 'az account set --subscription 80194c30-342a-4c69-b593-be125c916264'
        //sh 'az login'
   //     sh 'az aks get-credentials --resource-group sujanavmdemo --name sujanakube'
     //   sh 'kubectl apply -f k8s-deployment.yaml'
 
   // } 
    
  }

