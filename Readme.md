# Deploy Retrieval

Collection of Ansible playbooks to deploy the Retrieval HTTP API.


## About Retrieval

The retrieval serves recorded data from e.g. SwissFEL databuffer, HIPA archive and GLS archive
via a HTTP API.

Some installations like HIPA consist of one node, whereas SwissFEL databuffer consists of multiple nodes.

We use nginx as a reliable frontend for hot-switching to a new version.
Measurement shows no significant impact on performance because of this.


## Description of deployment

The playbook makes sure that:

* Java runtime is available
* Retrieval Jar file deployed
* Config files deployed
* Services set up and started


## Location of executables

The playbook takes the executable from `sf-daqbuf-33` in directory `/usr/share/nginx/html/distribute/retrieval/`.
This directory is used because our internal Artifactory server is not maintained since a long time and it is not
clear how to get a user account.
The above directory is made available via `https://data-api.psi.ch/distribute/retrieval` to all hosts for deployment
using the `nginx` on `sf-daqbuf-33` proxied through `data-api`.


## Deploy Retrieval

Deploy to sf-databuffer, sf-imagebuffer, hipa-archive and gls-archive:

```bash
ansible-playbook install-retrieval.yml
```
