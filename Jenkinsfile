#! /usr/bin/env groovy

@Library('shared-lib1')_


pipeline {
    agent any
    stages{
         
    /* stage('Create Project in JIRA'){
            steps{
             jira_create_project()
            }
  
 }
 stage('Create Issues in JIRA'){
     steps{
         jira_create_issues()
     }
 }*/
        stage('Checkout') {
            steps{
       git branch: 'Master', credentialsId: '8884589124', url: 'http://chenna@ec2-18-224-68-30.us-east-2.compute.amazonaws.com:7990/scm/dem/web_1.git'
   }
            }
        
        stage('Building & Packing')
        { 
            steps{
            building()
            }
        }
    
     stage('Code Analysis') 
           { environment {
             scannerHome=tool 'sonar scanner'
           }
              steps {
                echo 'starting sonarqube anaysis'
                 sonar()
                }
            }
          
  
  stage('QualityGate') {
      steps {
            echo 'starting quaity gates'          
          qualityGates() //this stage will fail if project quality doesn't meet its quality profile
      }
  }  
         
  
        
         stage("Upload to Nexus") {
             steps {
                  Nexus()
                     
             }
            }
         

/* stage('AnsibleRoleClone') {
            steps{
                script {
                    deployToEC2.gitClone("http://ec2-3-16-78-26.us-east-2.compute.amazonaws.com/Subinay/jenkinsinstallansiblerole.git")
                    }
                }
        }
        stage('DeployToEC2') {
            steps{
                script {
                    deployToEC2.playbook('jenkinsinstallansiblerole/host', 'jenkinsinstallansiblerole/DeployToEC2.yml')
                }
            }
        }*/
    
    }
}
/*post {
    always {
    notification(currentBuild.currentResult)
}
} */

