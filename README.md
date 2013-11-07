# Installation and configuration

Follow the instructions on [JuJu getting started page](https://juju.ubuntu.com/docs/getting-started.html).

# Usage

*Warning:* For EC2 deployment only us-west-2 zone is tested.
On other platforms you should ensure that Ubuntu instances have more 8GB free HDD space.

    git clone https://github.com/Altoros/cloudfoundry_charm.git
    juju deploy --repository cloudfoundry_charm/charms local:precise/cf-release --constraints "mem=7G cpu-cores=2 arch=amd64"

# CF cheat-sheet

    cf target http://api.<ip>.xip.io/
    cf login --password admin admin
    сf create-org <org-name>
    cf create-space <space-name>

Navigate to your app source dir.

    cf push

![](http://ad.retargeter.com/seg?add=1076364&t=2)
