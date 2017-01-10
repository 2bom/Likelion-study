[Deployment]How to deploy ruby on rails project using AWS, C9 and Git(Github).
===========

# 0. Prepare
  1. We have to get accounts for AWS, C9 and Git(Github).

# 1. Create rails project using C9

  \# In this example, we create rails project using C9.

  \# This part can be replaced with create rails project in local.

# 2. Create github repository

# 3. Connect and Upload rails project into new repo.
  \# In C9 project

  <pre><code>$ git init
$ git add .
$ git commit -m "commit message"
$ git remote add origin NEW_REPO'S_HTTPS_ADDRESS
$ git push origin master</code></pre>

# 4. Create AWS instance
  \# EC2, S3, Route 53

  1. Enter EC2 board
  2. Start to launch instance
  3. Select pre tier linux instance
  3. Add Security Group using HTTP(port 80)
  4. Set a key pair(create new pair)
  5. Creating instance completed
  6. Set name for new instance(optional)

# 5. Enter AWS by terminal
  1. Open terminal

  2. Get permission to enter AWS instance

    * This command line get some permission to enter aws instance by local terminal.
  <pre><code>$ chmod 400 DOWNLOAD-ROUTE/KEY-PAIR.pem</code></pre>

  3. Enter AWS instance
  <pre><code>$ ssh -i DOWNLOAD-ROUTE/KEY-PAIR.pem ec2-user@INSTANCE'S-IP-ADDRESS</pre></code>


  \# If you see like this, you did a good job.

       __|  __|_  )
       _|  (     /   Amazon Linux AMI
      ___|\___|___|

      https://aws.amazon.com/amazon-linux-ami/2016.09-release-notes/
      5 package(s) needed for security, out of 9 available
      Run "sudo yum update" to apply all updates.
      [ec2-user@ip-172-31-11-21 ~]$

  4. Update yum (in AWS instance)
    <pre><code>$ sudo yum update</pre></code>

  5. Download git (in AWS instance)

    * Search all contents related with git can download by yum.
    <pre><code>$ sudo yum search git</pre></code>

    * Download git-all.noarch.
    <pre><code>$ sudo yum install git-all.noarch</pre></code>

  \# If you see like this, you did a good job.

      $ git

      usage: git [--version] [--help] [-C <path>] [-c name=value]
                 [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
                 [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
                 [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
                 <command> [<args>]

      다음은 여러가지 상황에서 자주 사용하는 깃 명령입니다:
      ...


  6. Clone github repository (in AWS instance)
    <pre><code>$ sudo git clone REPOSITORY-URL</pre></code>

  7. Install RVM (in AWS instance)
    * Search and enter RVM public site

      > https://rvm.io/

    * Follow the information for installing RVM
    <pre><code>$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3</pre></code>
    <pre><code>$ curl -sSL https://get.rvm.io | bash -s stable</pre></code>

      \* **You have to check official web site before using this command lines. Because it can be changed by updates or any other reason.**


  8. Install ruby using RVM(in AWS instance)
    <pre><code>$ rvm install ruby-2.2.5</pre></code>
    \# Ruby version can be change.

    \# If you see like this, you did a good job.

        $ ruby -v
        ruby 2.2.5p319 (2016-04-26 revision 54774) [x86_64-linux]

  9. Install gems(in AWS instance)
    * Before install gems, should install bundle.
    <pre><code>$ gem install bundle</pre></code>
    * Install gems are used in this project
    <pre><code>$ bundle install</pre></code>

  10. Install passenger gem(in AWS instance)

    \# Passenger gem needs for running project.

    What is passenger?(https://rubygems.org/gems/passenger/versions/5.0.30)
    <pre><code>$ gem install passenger</pre></code>



  11. Install nginx(in AWS instance)
    * Enter project folder
      <pre><code>$ cd myapp</pre></code>
    * Command passenger install nginx.
      <pre><code>$ sudo passwd</pre></code>
      > (enter password)

      <pre><code>$ su</pre></code>
      <pre><code>$ passenger-install-nginx-module</pre></code>
    * Move toward solving problems(Do as what comments say to us).
      <pre><code>$ sudo chmod o+x "/home/ec2-user"</pre></code>
      <pre><code>$ passenger-install-nginx-module</pre></code>
      <pre><code>$ sudo yum search curl</pre></code>
      <pre><code>$ sudo yum install libcurl-devel.x86_64</pre></code>
      <pre><code>$ passenger-install-nginx-module</pre></code>
      <pre><code>$ sudo dd if=/dev/zero of=/swap bs=1M count=1024
$ sudo mkswap /swap
$ sudo swapon /swap</pre></code>
      <pre><code>$ passenger-install-nginx-module</pre></code>

      > Enter your choice (1 or 2) or press Ctrl-C to abort: ***1***

      > Please specify a prefix directory [/opt/nginx]: ***(just enter, setting for download route)***

# 6. Set environments
    Please edit your Nginx configuration file (probably /opt/nginx/conf/nginx.conf),
    and set the passenger_root and passenger_ruby configuration options in the
    'http' block, like this:

      http {
          ...
          passenger_root /home/ec2-user/.rvm/gems/ruby-2.2.5/gems/passenger-5.1.1;
          passenger_ruby /home/ec2-user/.rvm/gems/ruby-2.2.5/wrappers/ruby;
          ...
      }

    After you (re)start Nginx, you are ready to deploy any number of web
    applications on Nginx.



    $ exit
    $ vi /opt/nginx/conf/nginx.conf

    copy and paste into above the server {...}

    server {
        listen 80;
        server_name 52.78.6.128;
        passenger_enabled on;
        root /home/ec2-user/gangnam05-w1/public;
    }
    server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
        root   erb;
        index index.erb index.html.erb;
    }


    * modify project/gemfile (in c9)
    uncomment therubyracer

    $ bundle install
    $ git add
    $ git commit
    $ git push origin master

    * download modified project in aws instance
    $ git pull origin master


    $ rake db:migrate RAILS_ENV=production
    $ rake secret

 .... This document is not completed yet.
