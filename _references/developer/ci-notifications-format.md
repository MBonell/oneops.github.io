---
title: CI notification format
id: CI notification format
---

OneOps broadcasts the CI notifications to all configured sinks as well as to email recipients configured.
A CI notification json has a format like below sample:

``` json
{
    ts: "2016-01-01T15:51:42.183",
    cmsId: 1234,
    cloudName: "abc",
    severity: "warning",
    type: "ci",
    source: "ops",
    subject: "as-tomcat-compute-ssh:SSH Up is violated.",
    text: "compute-11031075-2 is in unhealthy state; Starting repair",
    nsPath: "/Org/as/prod/bom/tomcat/1",
    payload: {
        total: "6",
        oldState: "good",
        unhealthy: "5",
        eventName: "as-tomcat-compute-ssh",
        className: "bom.main.2.Compute",
        threshold: "SSH Up",
        state: "open",
        metrics: "{"avg":{"up":0.0}}",
        ciName: "compute-11031075-2",
        good: "1",
        newState: "unhealthy",
        status: "new"
    },
    timestamp: 1460404258633,
    environmentProfileName: "PROD",
    adminStatus: "active",
    manifestCiId: 58108355
}
```
The new state of a ci (payload.newState) could be any of below :

- notify
- unhealthy
- underutilized
- overutilized
- good

An "open" type of notification event (payload.state) is created in case a threshold/monitor is violated for a CI (component instance) - for example if cpu idle goes below 20


A matching close event notification is created in case a "reset" condition is met for a CI. - For example if cpu idle moves to  above 60


A unique notification can be identified by this combination - {cmsId + payload.eventName + payload.threshold}. Here the cmsId identifies a unique ci object - like one particular compute (or tomcat) instance. The ( payload.eventName + payload.threshold) identifies the monitor-threshold that got violated.


There will be a matching "close" notification event with the same {ciId + payload.eventName + payload.threshold} but with payload.state = 'close'

Here is the sample for a matching close event for above open event:

```json
{
    ts: "2016-01-01T19:51:42.183",
    cmsId: 1234,
    cloudName: "abc",
    severity: "info",
    type: "ci",
    source: "ops",
    subject: "as-tomcat-compute-ssh:SSH Up recovered.",
    text: "compute-11031075-2 is in good state.",
    nsPath: "/Org/as/prod/bom/tomcat/1",
    payload: {
        total: "6",
        oldState: "unhealthy",
        unhealthy: "1",
        eventName: "as-tomcat-compute-ssh",
        className: "bom.main.2.Compute",
        threshold: "SSH Up",
        state: "close",
        metrics: "{"avg":{"up":100.0}}",
        ciName: "compute-11031075-2",
        good: "5",
        newState: "good",
        status: "new"
    },
    timestamp: 146040231302183,
    environmentProfileName: "PROD",
    adminStatus: "active",
    manifestCiId: 2345
}
```
