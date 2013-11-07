## How to install JUJU on Ubuntu

```
sudo apt-get -y install python-software-properties
sudo add-apt-repository ppa:juju/pkgs
sudo apt-get update
sudo apt-get -y install lxc apt-cacher-ng libzookeeper-java zookeeper juju git
```

Create a SSH authorized/public key if you haven't yet
```
ssh-keygen -t rsa
```

Set AWS credentials
```
export AWS_ACCESS_KEY_ID=XXXXXXXX
export AWS_SECRET_ACCESS_KEY=YYYYYYYY
```

Now you can start working with JUJU. You'll need to edit `environments.yaml`. The easiest way it's to run `juju bootstrap`. It will show an error message but you can ignore it by now.
File will be located under `~/.juju/environments.yaml`
Edit it and add AWS access-key

Here is an example:
```
environments:
  cf-test:
    type: local
    control-bucket: juju-a14dfae3830142d9ac23c499395c2785999
    admin-secret: 6608267bbd6b447b8c90934167b2a294999
    data-dir: /home/your_user/some_dir
    default-series: precise
    access-key: XXXXXXXX
    secret-key: YYYYYYYY
    instance-type: m1.medium
```

Now you can bootstrap and check the status to see if it is running.
(It takes a little time to bootstrap). Alternatively you can check on the AWS Console.

```
$ juju bootstrap
$ juju status
# =>
  machines:
    0:
      agent-state: running
      dns-name: ec2-50-17-98-179.compute-1.amazonaws.com
      instance-id: i-57197f3a
      instance-state: running
```


