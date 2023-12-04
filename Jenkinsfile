pipeline {
  agent any
  stages {
    stage('S1 6719053N') {
      //Assume release environment setup is done here
      steps {
        echo 'Stage1_6719053N:Release Environment Preperation Completed'
      }
    }
    stage('S2 6719053N') {
      steps {
        sh 'docker stop WebApp_6719053N || true'
        sh 'docker rm -f WebApp_6719053N || true'
        sh 'docker run -d --name WebApp_6719053N -p 31200:80 wb1_image_6719053n'
        echo 'Stage2_6719053N: Release Container WebApp_6719053N Created Completed'
      }
    }
    stage('S3 6719053N') {
      parallel {
        stage('S3 6719053N API Test'){
          steps{
            //Assume API activities done here
            echo 'Stage3_6719053N:API Test Completed'           
          }
        }
        stage('S3 6719053N Scan Test'){
          steps{
            //Assume security scan test done here
            echo 'Stage3_6719053N:Scan Test Completed'
          }
        }
        
      }
    }
    stage('S4 6719053N') {
      steps {
        input('6719053N, proceed to release the work to the next phase?', parameters: [choice(name: 'ACTION', choices: 'Proceed\nAbort', description: 'Choose an action')])
      }
    }
    stage('S5 6719053N') {
      steps {
        if (params.ACTION == 'Proceed') {
          echo 'Stage5_6719053N:Work Release - Proceed to Next Phase'
        }
        if (params.ACTION == 'Abort') {
          echo 'Stage5_6719053N:Work Release - Stops'
        }
      }
    }
  }
}
