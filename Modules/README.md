# Modules

### Requirement for Modules

Automatic scaling instances of the App Engine serves the following purposes

* handling large scale user traffic
* handling traffic spikes 

However, Automatic scaling instances might not be suited for other computation tasks

* Always-listening Backend Services
* Batch jobs
* Long-running computing tasks

### Configuration

**URL**

A module can be configured with its own URL, which makes it accessible individually. A URL can be configured to be

* public: to allow external clients to access the module.
* private: to allow ONLY other modules to access the module internally.

### Deployment

The following deployment parameters of a module are independent from other modules

* *Time*: The time of deployment
* *Version*: The version of deployment

### Benefits

By using *modules*, an application could be architected in such a way that each of its component can be 

* developed independently
* configured and performance-tuned independently


