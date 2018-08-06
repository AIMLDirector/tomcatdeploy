node {
        stage("Main build") {
            checkout scm

            docker.image('centos').withRun('-u root --name testnode') {

              stage("Install Tomcat") {
                sh "/usr/bin/sudo -n yum install -y tomcat"
              }
            
              stage("starting server") {
                echo 'Testing...'
                sh '/usr/bin/sudo -n systemctl enable tomcat;/usr/bin/sudo -n /usr/libexec/tomcat/server start &'
              }

           }

        }

        // Clean up workspace
        step([$class: 'WsCleanup'])

}
