/* groovylint-disable CompileStatic */
// This is the Jenkinsfile for a project that creates a Debian package holding
// a portable version of VS Code with a number of extensions pre-installed and
// settings pre-configured

downloadLink = 'https://code.visualstudio.com/sha/download?build=stable&os=linux-x64'
extensionList = [
   'AdaCore.ada',
   'alphabotsec.vscode-eclipse-keybindings',
   'matepek.vscode-catch2-test-adapter',
   'ms-azuretools.vscode-docker',
   'ms-python.python',
   'ms-python.vscode-pylance',
   'ms-toolsai.jupyter',
   'ms-toolsai.jupyter-keymap',
   'ms-toolsai.jupyter-renderers',
   'ms-vscode.cmake-tools',
   'ms-vscode.cpptools',
   'ms-vscode.cpptools-extension-pack',
   'ms-vscode.cpptools-themes',
   'NicolasVuillamy.vscode-groovy-lint',
   'redhat.java',
   'redhat.vscode-xml',
   'RTI.omg-idl',
   'SonarSource.sonarlint-vscode',
   'twxs.cmake',
   'VisualStudioExptTeam.vscodeintellicode',
   'vscjava.vscode-gradle',
   'vscjava.vscode-java-debug',
   'vscjava.vscode-java-dependency',
   'vscjava.vscode-java-pack',
   'vscjava.vscode-java-test',
   'vscjava.vscode-maven',
   'webfreak.debug'
]

node {
   timeout(time:20, unit: 'MINUTES') {
      buildEnv = docker.image('ubuntu:20.04')
      buildEnv.inside('') {
         // cleanup any previous work
         sh 'rm -rf VSCode-linux-x64 vscode.tar.gz *.deb'

         // download, extract and cleanup
         sh "wget -O vscode.tar.gz ${downloadLink}"
         sh 'tar xf vscode.tar.gz'
         sh 'rm vscode.tar.gz'

         // setup portable mode
         sh 'mkdir VSCode-linux-x64/data'

         // install extensions
         for (extension : extensionList) {
            sh "VSCode-linux-x64/code --force ${extension}"
         }

         // setup default configuration

         // put into package

      // publish package
      }
   }
}
