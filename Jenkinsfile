        pipeline{
            tools{
                jdk 'java'
                maven 'maven'
            }
            agent none
            stages{
                stage('Checkout'){
                    agent any
                    steps{
                echo 'cloning...'
                        git 'https://github.com/meregabriel/DevOpsClassCodes.git'
                    }
                }
                stage('Compile'){
                    agent {label 'agent1'}
                    steps{
                        echo 'compiling...'
                        sh 'mvn compile'
                }
                }
                stage('CodeReview'){
                    agent {label 'agent1'}
                    steps{
                    
                echo 'codeReview...'
                        sh 'mvn pmd:pmd'
                    }
                }
                stage('UnitTest'){
                    agent {label 'agent2'}
                    steps{
                    echo 'Testing'
                        sh 'mvn test'
                    }
                    post {
                    success {
                        junit 'target/surefire-reports/*.xml'
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
