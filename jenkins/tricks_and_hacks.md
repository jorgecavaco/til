# Jenkins

* Obtain sh output:
`SOME_VAR = sh (
    script: 'git --no-pager show -s --format=\'%ae\'',
    returnStdout: true)`


* Obtain sh status code:
`SOME_VAR = sh (
    script: "git log -1 --pretty=%B | grep '\\[jenkins-full]'",
    returnStatus: true)`

---
Resources

* https://jenkins.io/doc/pipeline/steps/workflow-durable-task-step/#sh-shell-script
