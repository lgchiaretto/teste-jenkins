pipeline {
<<<<<<< HEAD
   agent any
   
   environment {

        CODE_COMMIT_INPUT = 0
        OPENSHIFT_PROJECT = "demo-dev"
        OPENSHIFT_BUILDCONFIG_NAME = "chiaretto-tam-pipeline"

    }
=======
  agent any
  stages {
    stage('Hello') {
      input {
        message 'Favor entrar a versão (commit) do código:'
        id 'Confirmar'
        parameters {
          string(name: 'CODE_COMMIT_INPUT', description: 'Versão de commit do código')
        }
      }
      steps {
        script {
          openshift.withCluster() {
            openshift.withProject("${OPENSHIFT_PROJECT}") {
              echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
              openshift.selector("buildconfig/${OPENSHIFT_BUILDCONFIG_NAME}").startBuild("--commit=master --wait=true --build-arg=AMBIENTE_CONTAINER=dev --env=VERSAO_CODIGO=${CODE_COMMIT_INPUT}").logs('-f')
>>>>>>> a3138d6bf85d85037ee7bc4f9e51794bde7f90d0

            }

          }
        }

      }
    }
  }
  environment {
    CODE_COMMIT_INPUT = 0
    OPENSHIFT_PROJECT = 'demo-dev'
    OPENSHIFT_BUILDCONFIG_NAME = 'dockerfile-corporativo-1-git'
  }
}