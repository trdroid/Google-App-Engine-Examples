# Modules

App Engine allows grouping instances and assigning each group a specific purpose. Each such group is known as a *module*. 

### Requirement for Modules

Automatic-scaling instances of the App Engine serves the following purposes

* handling large scale user traffic
* handling traffic spikes 

However, automatic-scaling instances might not be suited for other computation tasks

* Always-listening Backend Services
* Batch jobs
* Long-running computing tasks

### Configuration

**Configuring URL**

A module can be configured with its own URL, which makes it accessible individually. A URL can be configured to be

* public: to allow external clients to access the module.
* private: to allow ONLY other modules to access the module internally.

**Configuring Scaling Strategies**

A module can be configured with the following scaling strategies

* *Automatic Scaling*
* *Manual Scaling*: involves starting and stopping instances 
    * Using Cloud SDK within the app (or)
    * Calling an API from the app
* *Basic Scaling*: involves features of *Manual Scaling* + a configurable scheduler that can
    * start new instances, if necessary, in response to requests
    * stop idle instances after a configurable period of time

### Deployment

The following deployment parameters of a module are independent from other modules

* *Time*: The time of deployment
* *Version*: The version of deployment

### Benefits

By using *modules*, an application could be architected in such a way that each of its component can be 

* developed independently
* configured and performance-tuned independently


