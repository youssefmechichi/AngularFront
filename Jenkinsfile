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
		sh "sudo ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
		}
	    }
        }
	
      }
}
