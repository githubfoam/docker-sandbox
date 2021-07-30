# docker-sandbox

[![Ubuntu workflow](https://github.com/githubfoam/docker-sandbox/actions/workflows/ubuntu-workflow.yml/badge.svg?branch=master)](https://github.com/githubfoam/docker-sandbox/actions/workflows/ubuntu-workflow.yml)

Travis (.com)  branch:
[![Build Status](https://travis-ci.com/githubfoam/docker-sandbox.svg?branch=master)](https://travis-ci.com/githubfoam/docker-sandbox)  

Install Docker Engine
~~~
del Vagrantfile
vagrant init --template Vagrantfile.ansible.role.erb 
vagrant up  vg-docker-01
vagrant ssh vg-docker-01 (password:vagrant)

Supported platforms
https://docs.docker.com/engine/install/
~~~
