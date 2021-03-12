pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    agent none
      stages{
          stage('Checkoutt1'){
              agent any
              steps{
                  git 'https://github.com/devops-trainer/game-of-life.git'
              }
          }
          stage('Compile1'){
              agent any
              steps{
                  sh 'mvn compile'
              }
          }
          stage('UnitTest'){
              agent{label 'linux_slave'}
              steps{
                  git 'https://github.com/devops-trainer/game-of-life.git'
                  sh 'mvn test'
              }
              post{
                  always{
                      junit 'gameoflife-web/target/surefire-reports/*.xml'
                  }
              }
          }
          stage('Package'){
              agent any
              steps{
                  sh 'mvn package'
              }
          }
         
      }
    
}
