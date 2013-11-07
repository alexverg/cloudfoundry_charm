## Instaling JUJU with local charms

#### Juju
```
sudo apt-get -y install python-software-properties
sudo apt-add-repository ppa:juju/pkgs
sudo apt-get update
sudo apt-get -y install juju bzr
```

#### Charms and supporting scripts
```
bzr branch lp:~canonical-sig/+junk/cloudfoundry-server
bzr branch lp:~canonical-sig/+junk/cloudfoundry-server-dea
bzr branch lp:~canonical-sig/+junk/cf-mysql
bzr branch lp:~kirkland/+junk/drawbridge
bzr branch lp:~negronjl/+junk/ubuntu-latest-image
chmod +x ./ubuntu-latest-image
juju
echo "    default-image-id: `ubuntu-latest-image oneiric m1.large | grep Image | awk '{ print $3 }'`" >> ~/.juju/environments.yaml
echo "    default-instance-type: m1.large" >> ~/.juju/environments.yaml
```

#### Bootstrap
```
juju bootstrap
```

#### Deploy
```
juju deploy --repository charms cloudfoundry-server
juju deploy --repository charms cloudfoundry-server-dea
juju deploy --repository charms cf-mysql
```

#### Relationships
```
juju add-relation cloudfoundry-server cloudfoundry-server-dea
juju add-relation cloudfoundry-server cf-mysql
```

#### Scale
```
juju add-unit cloudfoundry-server-dea
juju add-unit cf-mysql
```

#### DrawBridge
```
cd drawbridge
vmc
vmc target <your hostname here>
vmc add-user
vmc push
```

#### Take it all down
```
juju destroy-environment
```
