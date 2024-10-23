node {
   def PROJET="thomas-forma/app:3.5"
   def IMAGE=$PROJET
   
    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
          }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID") { c ->
       
          }
    }

    stage('Push') {
       docker.withRegistry('https://registry.ludovic.io/' , 'thomas') {
              img.push 'latest'
              img.push()
          }
    }
   stage('compuse_up') {
       sh 'docker compose up --detach'
    }

}

