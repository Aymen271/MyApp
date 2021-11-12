pipeline {

    agent any


    stages {
      
       stage ('Pull') {
            steps {
		script{
		    checkout([$class: 'GitSCM' , branches: [[name: '*/master']],
			userRemoteConfigs: [[
			    url: 'https://github.com/Aymen271/MyApp']]])
               }
            }
        }
 
        stage ('Docker'){
           steps{
              script{
                  sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
	}
      }
      }
      stage('dockerHub') {
             steps{
                script{
                    sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                }
            }
        }
      }
      }
