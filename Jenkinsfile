node{
  def remote = [:]
  remote.name = 'oraclevm'
  remote.host = '152.67.160.182'
  remote.user = 'opc'
  remote.password = 'Muzammil073#'
  remote.allowAnyHosts = true
  stage('checkout') {
           checkout scm
  }  
  stage('step1'){
     sshPut remote: remote, from: 'sania021', into: '/home/opc'
  }
  stage('step2'){
    sshCommand remote: remote, command: "sudo sh /home/opc/sania021.sh"
  }
  stage('step3'){
    sshCommand remote: remote, command: "pwd"
  }
  stage('step'){
    sshCommand remote: remote, command: "mv /home/opc/sania021  /home/opc/sania021/"
  }
}
