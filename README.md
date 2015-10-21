Setup local development environment.  Installs Apache, MySQL, Ruby.  See main.yml for more details.

```
mkdir mycentos && cd mycentos
vagrant init bento/centos-6.7
vi Vagrantfile # IP編集
vagrant up
vagrant ssh
sudo yum -y install git
git clone https://github.com/kookaa/ruby-provisioning.git
cd ruby-provisioning
./run.sh
cd ~/workspace
bundle init
vi Gemfile
# rails の#をはずす
#:wq
bundle install
bundle exec rails new xxxapp --skip-bundle
cd xxxapp
vi Gemfile
#'therubyracer'の#をはずす
#:wq
bundle install
bundle exec rails g model Project title
rake db:migrate
bundle exec rails s -b 192.168.33.10
# web browsing http://192.168.33.10:3000/
```

If you need to update the environment, please follow instructions below.

```
cd
cd mycentos # Vagrantfileがあるフォルダに移動
vagrant up
vagrant ssh
cd ruby-provisioning
git pull --rebase
./run.sh
exec $SHELL -l
```


