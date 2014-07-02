Deploop Mcollective Agent
=========================

The Deploop system Agent for role facts deployment.

Usage
=====

This command insert on each /etc/puppet/puppet.conf node:

```
pluginsync=false  ==> deploop issue #2
factpath=/var/lib/puppet/facts.d/ ==> facts location for puppet
environment=production ==> built-in environment mechanism for puppet
```

```
mco find --with-agent deploop # for sanity checking
mco rpc deploop puppet_environment env=production --with-identity=host001
mco rpc deploop puppet_environment env=preproduction --with-identity=host002
mco rpc deploop puppet_environment env=test
 ```


The following command create the deploop fact into the agent folder /var/lib/puppet/facts.d
and update the facters file: /etc/mcollective/facts.yaml

```
mco rpc deploop create_fact fact='collection' value='production' --with-identity=host0001
mco rpc deploop create_fact fact='category' value='batch' --with-identity=host001
mco rpc deploop create_fact fact='role' value='nn1' --with-identity=host001
mco rpc deploop create_fact fact='entity' value='flume kafka whatever' --with-identity=host001
 ```







