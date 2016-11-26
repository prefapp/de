de (docker execute) 
===================

**de** runs commands in a docker container associated to your code project.

Requirements
------------
- docker
- perl
- YAML Perl module.   
For debian/ubuntu:  
```sudo apt-get install libyaml-perl```


To get started
---------------

- Install **de**:
```
sudo curl https://raw.githubusercontent.com/prefapp/de/master/de -o /usr/local/sbin/de && \ 
sudo chmod 755 /usr/local/sbin/de
```

- Configure your project preferences in a yaml file (.de) inside your project home
For example:

```yaml
image: myrailsapp
env:
  RAILS_ENV: production
links:
  - mysql:mysql
ports:
  - 80

```

Have fun!

For example, if you have a rails application, run the test inside your container __from outside__

```
spock@enterprise:~/proxectos/panel-v2$ de rake test
Run options: --seed 54518

# Running:

.................EE..EEEE....E....E

Finished in 3.275538s, 10.6853 runs/s, 13.1276 assertions/s.


```

- If you want run commands as root user inside container (very useful in some situations)
```
spock@enterprise:~/proxectos/panel-v2$ de -C -R  bundle install
Don't run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-root users on this machine.
Fetching gem metadata from https://rubygems.org/.........
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Using rake 10.4.2
Using i18n 0.7.0
Using json 1.8.3
Using minitest 5.8.1
Using thread_safe 0.3.5
Using tzinfo 1.2.2
Using activesupport 4.2.4
Using builder 3.2.2
Using erubis 2.7.0
Using mini_portile 0.6.2
Installing nokogiri 1.6.6.2
Installing rails-deprecated_sanitizer 1.0.3
Installing rails-dom-testing 1.0.7
Installing loofah 2.0.3
Installing rails-html-sanitizer 1.0.2
Installing actionview 4.2.4
Installing rack 1.6.4
Installing rack-test 0.6.3
Installing actionpack 4.2.4
Installing globalid 0.3.6
Installing activejob 4.2.4
Installing mime-types 2.6.2
Installing mail 2.6.3
Installing actionmailer 4.2.4
Installing activemodel 4.2.4
Installing arel 6.0.3
Installing activerecord 4.2.4
....
```
-**-C** is set to specify that we want **commit** container changes into image


The config file
-----------------

.de is a yaml config file, generated in the root of your project. 

```yaml
image: docker image needed by your project
working_dir: volume path to the project source code, inside the container, by default '/home/<my_project_name>'
ports: [list of ports to connect your container]
volumes: [list of volumes to connect to your container]
links: [ array of external containers to to link to ]
env: Hash of environment variables needed to configure your application
```

