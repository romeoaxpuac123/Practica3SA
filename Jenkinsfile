pipeline {
    agent any
    stages {

		stage('Copiando Archivo') {
            steps {
                sh 'echo mv default.rb /home/workstation/chef-repo/cookbooks/sample/recipes/'
            }
        }
		stage('Cargando Receta') {
            steps {
                sh 'echo cd /home/workstation/chef-repo/cookbooks; knife cookbook upload sample;'
            }
        }
		stage('añadiendo a nodo cliente 1') {
            steps {
                sh 'echo cd /home/workstation/chef-repo/cookbooks; knife node run_list add chef-node recipe[sample::default]'
            }
        }
		stage('añadiendo a nodo cliente 2') {
            steps {
                sh 'echo cd /home/workstation/chef-repo/cookbooks; knife node run_list add chef-node2 recipe[sample::default]'
            }
        }
		stage('Corriendo cliente 1') {
            steps {
                sh 'echo cd /home/workstation/chef-repo/cookbooks; knife bootstrap 192.168.88.134 --ssh-user  geekflare password 1234 --node-name chef_node'
            }
        }
		stage('Corriendo cliente 2') {
            steps {
                sh 'echo cd /home/workstation/chef-repo/cookbooks; knife bootstrap 192.168.88.135 --ssh-user  geekflare password 1234 --node-name chef_node2'
            }
        }
		
			
    }
}
