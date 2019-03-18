# Logging & Monitoring Policy

Logging and monitoring are an integral part in not only developing an application
but also maintaining and securing it. The importance and effectiveness of
logging is not limited to applications but also applies to access of sensitive
or business critical data.

The below document sets out guidelines for logging application and access
events.


## Application Logs

All new applications deployed and managed by DVELP in a production environment
and unless expressly requested by a client, should send application logs to
[Papertrail](https://papertrailapp.com/) and errors to [Sentry](https://sentry.io/)
inline with our [diagnostics guidelines](/guides/environments/diagnostics.md).

Application logs on Papertrail remain searchable for up to 1 week and persist
archived for up to a year.


## Access Logs

The following platforms have been identified as requiring detailed access log
management:

* Amazon Web Services (AWS)
* Cloudflare
* Charlie HR [Not available]
* GitHub [Partially available]
* Google Cloud Platform (GCP)
* GSuite (Google Apps)
* Harvest
* Heroku [Not available]

With the exception of those where logging is not currently available, each of
the above applications should log the following events:

* Sign-in
* Failed sign-in
* Resource creation
* Resource deletion
* Identity Access Management; create, update, destroy

These logs are reviewed on an ad-hoc basis if a security breach is suspected or
detected.


## Device Logs

All logging performed on devices, both laptops and mobiles is not accessible
remotely or stored centrally.


## Clock Syncronisation

All production applications managed by DVELP are deployed to Heroku. Heroku is
responsible for Clock NTP synchonisation to help ensure logs are written with
the correct date and timestamp.

