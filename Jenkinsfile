pipeline {
	agent {label params['agent']}
	parameters {
			string(name: 'diskspace', defaultValue: '')
			}
	environment {
			threshold = '70'
			}
	stages {
		stage ('Check Disk Space') {
			steps{
				script {
					def diskspace1 = powershell(returnStdout: true, script:"""echo(((((Get-WmiObject Win32_LogicalDisk -Filter "DeviceID='C:'").Freespace)/(Get-WmiObject Win32_LogicalDisk -Filter "DeviceID='C:'").Size))*100)""")
					
					env.diskspace = diskspace1

					println diskspace1
				}
			}
		}

		stage ('Stage 2') {
			when{ expression{ env.diskspace >= env.threshold} }
			steps {
				echo "${env.diskspace}"
				}
			}

		stage ('Stage 3') {
			steps{
				echo "${env.diskspace}"
			}
		}
	}
}
