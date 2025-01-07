pipeline {
    agent any

    parameters {
        booleanParam(name: 'RUN_BASIC_ENV', defaultValue: true, description: 'Run Basic Environment Check')
        booleanParam(name: 'RUN_FILE_OPS', defaultValue: true, description: 'Run File Operations Test')
        booleanParam(name: 'RUN_NETWORK_TEST', defaultValue: true, description: 'Run Network Connectivity Test')
        booleanParam(name: 'RUN_BUILD_SIM', defaultValue: true, description: 'Run Build Simulation')
    }

    stages {
        stage('Basic Environment Check') {
            when {
                expression { return params.RUN_BASIC_ENV }
            }
            steps {
                sh '''
                echo "=== Basic Environment Check ==="
                echo "Current Directory: $(pwd)"
                echo "Logged-in User: $(whoami)"
                uname -a
                df -h
                '''
            }
        }

        stage('File Operations Test') {
            when {
                expression { return params.RUN_FILE_OPS }
            }
            steps {
                sh '''
                echo "=== File Operations Test ==="
                echo "This is a test file for Jenkins job." > testfile.txt
                echo "Contents of the test file:"
                cat testfile.txt
                mv testfile.txt renamed_testfile.txt
                echo "File renamed to renamed_testfile.txt"
                rm renamed_testfile.txt
                echo "File deleted: renamed_testfile.txt"
                '''
            }
        }

        stage('Network Connectivity Test') {
            when {
                expression { return params.RUN_NETWORK_TEST }
            }
            steps {
                sh '''
                echo "=== Network Connectivity Test ==="
                ping -c 4 google.com
                curl -I https://www.google.com
                echo "Network connectivity test completed!"
                '''
            }
        }

        stage('Build Simulation') {
            when {
                expression { return params.RUN_BUILD_SIM }
            }
            steps {
                sh '''
                echo "=== Build Simulation ==="
                mkdir -p build
                cd build
                touch main.o utils.o program.bin
                echo "Build files created:"
                ls -la
                cd ..
                rm -rf build
                echo "Build simulation completed!"
                '''
            }
        }
    }
}
