---
title: Running OneOps in Production
id: "running-OneOps-In-Production"
---
Use **OneOps to deploy OneOps in production**, so you get all the benefits of OneOps in managing your application refer this article. [](../references/#oneops-manages-oneops )

See also

  * Follow these general prescribed [practices]({{site.baseurl}}/{{site.contexts.user}}best-practices)
  * We can help , contact us <span class="button icon-slack"><a href="{{ site.slack_url }}" target="_blank">{{ site.slack_channel }}</a></span>
  

## Deploy in redundant mode.

OneOps backend applications are primarily *java web apps* deployable on *separate tomcats* or in *single* tomcat with *multiple artifacts*. For example you can deploy *adapter,transistor,transmitter,controller* apps on one tomcat, deploy the other apps on separate tomcat.

* Choose multiple fault zones.

You can deploy like

| WebApps|Platform|
|--------|---------|
|adapter,transistor,transmitter,controller| Tomcat
|sensor,opamp|Tomcat|
|User DB,CMS DDB |Postgres |
|elastic search | es |
|amq| Messaging Platform |
|opsmq|OpsMQ|
|daq|Cassandra|

See also [architecture-diagram](../key-concepts/#oneops-system-architecture)


## Use Command Line Interface
* Install OneOps CLI to perform any control actions from command line or search.

## Configure DB backups
* You can use gluster fs to set up a *store* to back up cms db.


## Use security groups.
For each platform use ports which are required for application to work.

## Use Elastic Search Kibana Logstash

* Set up an elastic search to ship your web logs or other logs for troubleshooting.
* More details coming.

## Avoid manual changes :
Anything **manual**  you do to make things work, will get overwritten in next deployment. Be sure to make change to design,transition configuration so that changes are not lost.
