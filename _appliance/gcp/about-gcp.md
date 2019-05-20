---
title: [GCP node overview]
keywords: gcp,appliance,overview
tags: [cloud,vm]
last_updated: tbd
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
Google Cloud Platform (GCP) can provide memory and CPU for your ThoughtSpot
instance.

Your database capacity will determine the number of instances you'll need and
the instance network/storage requirements. In addition, you can go with multiple
virtual machines (VMs) based on your dataset size.

You will need to setup the appropriate Firewall Rules in your GCP environment
for your ThoughtSpot deployment. See the [GCP Firewall Rules](https://cloud.google.com/vpc/docs/firewalls)
article for configuration details.

You can find more information about appropriate network policies for your
ThoughtSpot deployment in the [network ports reference]({{ site.baseurl}}/appliance/firewall-ports.html#).

## A little about GCP

GCP is a secure cloud services platform offered by Google. Using
ThoughtSpot on GCP allows you to easily add instances as your dataset grows.
You can do everything you’d normally want to do in a traditional data center
with GCP. It features an on-demand delivery of IT resources and applications
via the Internet. When you are connected to an instance, you can use it just
like you use any other server.

Using GCP lets you develop and deploy applications faster since there is no need
to manage hardware. Therefore, it is easy to scale and manage computing
capacity.

The ThoughtSpot image deploys on [Google Compute
Engine](https://cloud.google.com/compute/docs/), the GCP platform for creating
and running VMs (_instances_) on Google Cloud infrastructure. GCP
and Google Compute Engine use [Identity and Access Management
(IAM)](https://cloud.google.com/iam/) roles to manage permissions to resources.
Google Compute engine instances and persistent disks are [zonal
resources](https://cloud.google.com/compute/docs/regions-zones/), and therefore
must be in the same zone to work together.  