de (docker execute) 
===================

**de** runs commands in a docker container associated to your code project.

Requirements
------------
- perl
- YAML Perl module
```apt-get install libyaml-perl```


To get started
---------------

- Install **de**:
```
sudo curl https://raw.githubusercontent.com/prefapp/de/master/de -o /usr/local/sbin/de && \ 
sudo chmod 755 /usr/local/sbin/de
```

- Create a container associated to your project

In a ruby project, for example , from de root of your project run:

```
spock@enterprise:~/proxectos/panel-v2$ de -a start -i ruby:2.2 -p 80 
Creating container panel-v2_26...5bb262b9a995ab87ab7e254b138152c0a22ea40dba355ccc29294c8b3b4af84f
```

- Have fun!

For example run the test inside your container __from outside__

```
spock@enterprise:~/proxectos/panel-v2$ de rake test
Run options: --seed 54518

# Running:

.................EE..EEEE....E....E

Finished in 3.275538s, 10.6853 runs/s, 13.1276 assertions/s.


```

- If you want run commands as root user inside container (very useful in some situations)
```
spock@enterprise:~/proxectos/panel-v2$ de -R bundle
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

- Remove your dev container:
```
spock@enterprise:~/proxectos/panel-v2$ de -a rm 
Removing container ...panel-v2_26

```

The config file
-----------------

.de is a yaml config file, generated in the root of your project. 

Let 'de' create it for your at **de start**

```yaml
project: project name
image: docker image name needed by your project
container: container name associated, if not exists 'de' can create it
project_volume: volume path to the source code project, inside the container, by default '/home/my_project'
container_username: user in container to manipulate your project
container_group: container user group
homedir: container homedir
user_id: user_id of the container_user (by default your host user_id)
group_id: group_id of the container_group (by default your host group_id)
ports: [list of ports to connect your container]
```

