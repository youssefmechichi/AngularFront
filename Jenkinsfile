pipeline
{
    agent any
      stages {
        stage('PULL') {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                      userRemoteConfigs: [[
                          credentialsId: 'github_id',
                          url: 'https://github.com/youssefmechichi/AngularFront.git']]])
                }
            }
        }
        stage ('BUILD') {
	    steps{
		script{
		sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml -e ansible_become_password=181JMT2801"
		}
	    }
        }
	stage('docker'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml -e ansible_become_password=181JMT2801"
                }
            }
        }
        
         stage('docker-registry'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml -e ansible_become_password=181JMT2801"
                }
            }
        }
        
	
      }
}
