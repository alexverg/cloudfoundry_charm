## Instaling ruby

Option #1 (from package)

```
apt-get install -y ruby1.9.3 build-essential libcurl4-openssl-dev
```

Option #2 (with rbenv)

```
# Ruby
if [ ! -d ~/.rbenv ]; then
    git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
    git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
    echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
    . ~/.bash_profile
fi

rbenv install 1.9.3-p392
rbenv global 1.9.3-p392
gem install bundler --no-rdoc --no-ri
rbenv rehash
```