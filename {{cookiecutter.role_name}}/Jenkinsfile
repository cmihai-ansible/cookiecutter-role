
node() {
  stage ("Checkout scm") {
                checkout scm
        }

        stage ("install ansible and molecule") {
                sh """
                pip3 install --user --upgrade molecule[docker] ansible yamllint ansible-lint
                """
        }

        stage ("molecule lint") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule lint -s kvm
                """
        }

        stage ("molecule create") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule create -s kvm
                """
        }

        stage ("molecule converge") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule converge -s kvm
                """
        }

        stage ("molecule idempotence") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule idempotence -s kvm
                """
        }

        stage ("molecule verify") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule verify -s kvm
                """
        }

        stage ("molecule destroy") {
                sh """
                export PATH="~/.local/bin:$PATH"
                ~/.local/bin/molecule destroy -s kvm
                """
        }
}
