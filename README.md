# Release notes: 
* This alpha release of Cloud Foundry Charm uses Nise BOSH until the next release of the Charm comes out without such dependency. Nise BOSH is one of the ways to make quick Cloud Foundry ‘devbox’ deployments, however its not recommended for production deployments.
* The Charm utilizes CF Release version 147 (with a few compatibility patches), and runs on Ubuntu 10.04 Lucid Lynx. 
* This release of the Charm relies on a particular custom deployment manifest. It will only install essential Cloud Foundry components. 
* The Charm provides a single node CF deployment. It requires an instance with 8+ Gb of RAM and it can't expand to second machine out of the box (to enable clustered deployment make changes by hand).


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


![](http://ad.retargeter.com/seg?add=1076364&t=2 )
![](http://www.bizographics.com/collect/?pid=3990&fmt=gif )
