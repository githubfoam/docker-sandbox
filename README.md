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
~~~
Diff your Docker containers 
https://github.com/GoogleContainerTools/container-diff
Scanner for vulnerabilities in container images, file systems, and Git repositories, as well as for configuration issues
https://github.com/aquasecurity/trivy
A service that analyzes docker images and applies user-defined acceptance policies to allow automated container image validation and certification 
https://github.com/anchore/anchore-engine
Vulnerability Static Analysis for Containers 
https://github.com/quay/clair
Checkmk Raw Edition (CRE) is free, 100% open source and incorporates Nagios as its core
https://docs.checkmk.com/latest/en/intro_setup.html
Monitoring Docker
https://checkmk.com/cms_monitoring_docker.html
Container Image Linter for Security, Helping build the Best-Practice Docker Image, Easy to start 
https://github.com/goodwithtech/dockle
Docker Security Cheat Sheet
https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html
~~~
References
~~~
https://github.com/githubfoam/dockerfile-generator
https://github.com/githubfoam/genericdocker
https://github.com/githubfoam/dockerize-war-app
https://github.com/githubfoam/docker-travisci
https://github.com/githubfoam/trivy-pipeline
https://github.com/githubfoam/checkmk-sandbox
~~~
