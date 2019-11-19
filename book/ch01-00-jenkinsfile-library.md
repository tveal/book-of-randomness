[//]: # (start {createChapterHeader} following is GENERATED)
# 1.0 Jenkinsfile Library
[//]: # (end of generated)

[//]: # (start {createNav} following is GENERATED)
[![](img/Open_Iconic_arrow_circle_left.png "Previous: 0.0 Contributing Doc")](./ch00-00-contributing-doc.md "Previous: 0.0 Contributing Doc")
[![](img/Open_Iconic_home.png "Home")](../README.md "Home")

[//]: # (end of generated)

## Import a Jenkins Library without Global Jenkins Settings

**Jenkins library structure**
```
(root)
+- vars/
|   +- init.groovy
```
**init.groovy from library**
```groovy
def call(String name = 'Honua') {
    env.GREETINGS = "Aloha $name!"
}
```

**Jenkinsfile in another project**
```groovy
library(
    identifier: 'custom-jenkins-library@master',
    retriever: modernSCM(
        [
            $class: 'GitSCMSource',
            remote: 'https://github.com/tveal/fake-repo-changeme.git',
            credentialsId: 'jenkins-creds-id'
        ]
    )
)

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                script { init() }
            }
        }
        stage('Greetings') {
            steps {
                echo "$GREETINGS" // Aloha Honua!
            }
        }
    }
}
```

Resources
- https://jenkins.io/doc/book/pipeline/shared-libraries/
- https://jenkins.io/doc/book/pipeline/syntax/

[//]: # (start {createNav} following is GENERATED)
[![](img/Open_Iconic_arrow_circle_left.png "Previous: 0.0 Contributing Doc")](./ch00-00-contributing-doc.md "Previous: 0.0 Contributing Doc")
[![](img/Open_Iconic_home.png "Home")](../README.md "Home")

[//]: # (end of generated)
