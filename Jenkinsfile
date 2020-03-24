pipeline {
   agent any
   
   environment {

        CODE_COMMIT_INPUT = 0
        OPENSHIFT_PROJECT = "demo-dev"
        OPENSHIFT_BUILDCONFIG_NAME = "chiaretto-tam-pipeline"

    }


   stages {
      stage('Hello') {
          
          input {

                message "Favor entrar a versão (commit) do código:"
                ok "Confirmar"
                parameters {
                    string(name: 'CODE_COMMIT_INPUT', description: 'Versão de commit do código')
                }}
          
          
         steps {
            
            script {
              openshift.withCluster() {
                  openshift.withProject("${OPENSHIFT_PROJECT}") {
                  echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
                  openshift.selector("buildconfig/${OPENSHIFT_BUILDCONFIG_NAME}").startBuild("--commit=master --wait=true --build-arg=AMBIENTE_CONTAINER=dev --env=VERSAO_CODIGO=${CODE_COMMIT_INPUT}").logs('-f')
                    
                  }
                 
              }
            }
         }
      }
    }
}
