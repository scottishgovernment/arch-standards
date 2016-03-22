# Domain Management

<!-- N.B. content copied from gov.uk on 13/08/2015. -->


## Purpose

This document describes the domain controls and procures in place to manage the delivery of transactional serves on the mygov.scot web domain. Supporting guidance is also provided relating to operation of DNS for these services.

<div style="color: #9F6000; background-color: #FEEFB3; font-size: 26px; border-style: solid; border-width: 2px; padding: 5px;">&#10148; Please note this document is currently in <strong>draft</strong> status and may be subject to change.</div>


## Contents

<!--TOC max3-->


## Revision History

| Version       | Issued     | Comments
| -             | -          | -
| Initial Draft | 14-08-2015 | Created initial draft from GSD content.
| Second Draft  | 17-08-2015 | Updated to remove duplication and reflect Scottish context.


## Domain name strategy for "Digital First" services

The Scottish Government offers a number of different digital services to citizens. While the start and end of a user's journey will be on mygov.scot, the service itself will typically be hosted elsewhere, and will need a different domain name as a result. This document describes the use of `service.mygov.scot` subdomains for hosting digital services.

> Note: This document is written as a 'standard', and as such uses the words MUST, SHOULD, MAY and MUST NOT as defined in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

### One entry point to each digital service

Every digital service offered by the Scottish government must have a single, well-known place on the web where users can locate and use the service. For public-facing services that well known place will be the relevant start page on mygov.scot – <mark>for instance, the DVLA’s tax disc service is at https://www.gov.uk/tax-disc</mark>.

Service Managers must not advertise any URL other than that of the mygov.scot start page as the starting point for the relevant service. This is what gets advertised, whether digitally or in other media.

The start page URL for a given service will be allocated by the Digital Public Services & Business Transformation division (DPS&BT) based on discussions with the Service Manager and analysis of user behaviour, search referrals and other relevant data.

The service itself will be provided on a URL of the form `www.{service-name}.service.mygov.scot`.

### Internal services, intranets and extranets

Services designed for an internal audience should also live on a domain of the form `{service-name}.service.mygov.scot` but do not need a start and end page on mygov.scot.

> <mark>The Cabinet Office runs a service for those involved in the Controls processes. That is not a public facing service so does not have a start page on mygov.scot, but as a new government service it lives on the relevant `service.mygov.scot` domain.</mark>


## The service subdomain lifecycle

To make sure that the right user journey (appropriate start/end pages, clear domain names) are set up for a new service it’s important that you engage with the mygov.scot team within DPS&BT early.

You can start the service domain name process by emailing <mark>gdsapprovals@digital.cabinet-office.gov.uk</mark> who will discuss with you the best name for your Service Domain and the start pages on mygov.scot.

While you are waiting for this process, you should start looking at where you will host the DNS, as DPS&BT will delegate control of your Service Domain to you. You should read more about delegating DNS for Service Domains here which will prepare you for the next step.

Once your service has an agreed name, you will need to supply the following information to your DPS&BT contact who will put you in touch with the DPS&BT Infrastructure Team to arrange delegation.

1. Service name, e.g. `{service-name}.service.mygov.scot`
2. DNS servers to delegate to (ask your technical team to see the guidance on DNS delegation)
3. Date you need it by (at least 5 working days’ notice)

<mark>If you are intending to use the “Managed DNS” product offered by Dyn, then you will need to give as much notice as possible, as Dyn is currently used to manage the main service.mygov.scot DNS domain. Dyn requires a signed letter of authorisation from DPS&BT and work on their systems in order to manage sub-zones of service.mygov.scot via other customer accounts – this may take additional time to arrange.</mark>


### Creating a service subdomain

The transactional part of a service -- the dynamically generated pages where users interact with the service -- will typically not be hosted on the `www.mygov.scot` domain. That means that each service needs its own domain name for the transactional part of the service.

> Note: This does not apply to the set of interactive tools on mygov.scot <mark>known as 'smart answers'</mark> which are developed and maintained by DPS&BT in partnership with other government departments.

<mark>For all new digital government services going live from 1 April 2013</mark>
DPS&BT will create a domain name of the form `{servicename}.service.mygov.scot` (where "servicename" is a plain English description of the service agreed between the relevant dept/agency and the Government Digital Service). This will introduce consistency across central government domains for digital services and remove the dependency on departmental subdomains (which are of course vulnerable to machinery of government changes).

The process of obtaining a `service.mygov.scot` subdomain begins when the service manager asks for a subdomain to be created via the <mark>mygov.scot service desks’s government contact form</mark>.  Subdomains of `service.mygov.scot` SHOULD describe the service (e.g. <mark>`lastingpowerofattorney.service.gov.uk`</mark>) and should not contain the name of the service owning department or agency (e.g. <mark>`ministryofmagicwandregistration.service.gov.uk`</mark>)

The service-owning dept/agency will be given delegated authority to manage the domain and its subdomains, although in some cases this work will be carried out by third party suppliers.

### Decommissioning a service subdomain

If your service should need to wind down for any reason, you MUST ensure continued useful service and information for users by:

* continuing to use SSL
* serving a redirect from your service to the mygov.scot start page

For services that have been live for less than 6 months, you MUST continue to do the above for the remainder of a year total. For services that have been live longer than that you MUST continue to do the above for a further 12 months or until the expiry of the current SSL certificate, whichever comes first.

The mygov.scot start page will be amended to explain that the service is no longer running, and cease to provide a start button pointing at the defunct service.


## [Operating a service.mygov.scot sub-domain](https://www.gov.uk/service-manual/operations/operating-servicegovuk-subdomains.html)

### Managing DNS records

Once a domain name for a service has been agreed, the DPS&BT Infrastructure Team allocates service.mygov.scot domain names by delegating control to the team running the service. The team should provide the details of nameservers and DPS&BT will delegate `{service-name}.service.mygov.scot` to those nameservers. At that point the service team will be able to manage the detailed configuration of which servers the domain name points to, and so on.

The model for service.mygov.scot domains requires that you provide your own DNS servers which can respond to requests for `{something}.{servicename}.service.mygov.scot`. It is not necessary that you run and manage your own separate DNS servers:

1. There are service providers on GCloud who will provide DNS Hosting with a web-interface for you to manage your DNS records.
2. Many infrastructure hosting providers also provide DNS services for the use of their customers.
3. As a last resort (or for larger services) you may wish to ask the supplier to provide DNS services by any means they consider reasonable (including utilising options 1 and 2 above).

#### Why do we do this?

It is likely that as you build and iterate your service you will need to make a number of changes to its configuration. You might introduce load balancers or content delivery networks, you may move hosting providers, or your provider might need to change the IP addresses that your servers are assigned. In any of those cases it is important that your team is able to quickly respond to the situation and make any relevant changes with as few intermediaries as possible. By delegating control DPS&BT ensures that control is in the hands of the service team and not blocked by a central authority.

### Service subdomains

This section gives some guidance about which subdomains a service manager should create once they have been given control of `servicename.service.mygov.scot`.

**Maximum number of visible subdomains**

The user-facing live service SHOULD be operated using at most three user-visible subdomains of `servicename.service.mygov.scot`:

* `www.servicename.service.mygov.scot` is for the public facing, dynamic web pages that make up your service.
* `assets.servicename.service.mygov.scot` is for assets such as static images and shared JavaScript files needed to run your live service (note: written content about the service, such as guides to eligibility or detailed guidance for applicants, SHOULD be on mygov.scot)
* `admin.servicename.service.mygov.scot` is for features that enable non-technical staff to run the service (eg contact centre staff might use this subdomain to access and process work items where human judgement is needed)

You SHOULD NOT create separate domains for application programming interfaces (APIs) unless there’s a really good reason to have a completely separate domain. (<mark>Really good reasons are few and far between.</mark>)

Service managers should notify the DPS&BT technical architects (via your <mark>transformation team contact</mark>) if you intend to create user-visible subdomains other than the three listed above. <mark>We’re developing some patterns</mark> for more unusual system designs as well as for mainstream transactional services, and we’re always up for a discussion about exceptions and edge cases.

**Usernames and passwords**

If the service is a private alpha or private beta release then it should be protected by a username and password known only to the development team and the users who are testing the service. If a service, or part of a service, is a public alpha or beta releases then it should be clearly marked as such with a text label on every page (ie don’t use an image containing the word alpha or beta) and in every API response.

**Multiple environments**

It is good practice to have multiple 'environments' for the development, testing and live (aka production) versions of any service. The [development and testing environments](/service-manual/making-software/sandbox-and-staging-servers.html) allow the team to assess the correctness and quality of the service before it goes live. Typically, the subdomains used to access a development or testing instance of the service are structured in the same way as the subdomains used in the live version of the service.

Therefore, you MAY [create other subdomains](/service-manual/domain-names/service-subdomain-names.html) of `servicename.service.mygov.scot` for use in testing and development, such as `www-preview.` and `www-dev`, or `www.preview.` and `www.dev.`. If there's a compelling reason to use a non `.mygov.scot` domain for testing and/or development subdomains, that’s also acceptable.

Regardless of the domain name used, web-based services on testing and development domains (including APIs) should be protected by a username and password along the same lines as private alpha and beta releases.

### Cookies

Cookies used on `www.servicename.service.mygov.scot` and `admin.servicename.service.mygov.scot` MUST be scoped to the originating domain only. Cookies MUST NOT be scoped to the domain `servicename.service.mygov.scot`.

Cookies SHOULD NOT be used on `assets.servicename.service.mygov.scot` (they [introduce a browser overhead that slows down the response time for users](https://developer.yahoo.com/performance/rules.html#cookie_free) without providing any benefit for the service manager).

Cookies MUST be sent with the `Secure` attribute and SHOULD, where appropriate, be sent with the `HttpOnly` attribute. These flags [provide additional assurances about how cookies will be handled by browsers](https://en.wikipedia.org/wiki/HTTP_cookie#Secure_and_HttpOnly).

### robots.txt and root level redirections

mygov.scot is the place for users to find all government services, so it’s important to ensure that users always start on the relevant mygov.scot page, rather than a different or duplicate start page on `www.servicename.service.mygov.scot`.

As a result, services need to ask search engines not to index pages on their domains, so that the relevant mygov.scot page and the service domain don’t compete with each other in search engine results. This can be achieved by redirecting users to the relevant mygov.scot start page if they go directly to the service’s domain name, and by asking search engines not to index pages on the service’s domain name. Therefore, every service hosted on a service.mygov.scot domain MUST:

* have a `robots.txt` file on the `www`, `admin` and `assets` subdomains asking search engines not to index any part of the site. Example content for `robots.txt` is given below, and more details can be found on [The Web Robots Pages](http://www.robotstxt.org/faq/prevent.html):

      User-agent: *
      Disallow: /

* have an HTTP 301 redirection from the top-level index page of the `www` and `assets` subdomains to the relevant start page on mygov.scot. (Note: this means that the service start page on mygov.scot SHOULD NOT link to the root of the `www` domain.)

### [Asset hosts](https://www.gov.uk/service-manual/domain-names/asset-hosts.html)

To provide the fastest possible experience for our users it’s usually a good idea to serve assets (stylesheets, JavaScript, images) from a separate domain name. That will enable the web browser to fetch more elements of the page in parallel, and also make it straightforward to remove cookies and other extraneous information from the HTTP responses for assets.

You should not use the asset host that we use for www.mygov.scot to load your assets. The files provided there are only guaranteed to work for www.mygov.scot and could change without notice in ways that would break other services that are using them. Instead you should host any assets you rely on within your service.

We recommend a hostname such as:

`assets.{service-name}.service.mygov.scot`

### Origin servers for CDN-based provider of DDOS protection

If you have contracted with [CDN](https://en.wikipedia.org/wiki/Content_delivery_network)-based [DDOS](https://en.wikipedia.org/wiki/DDOS#Distributed_attack)-protection suppliers then you should register these additional subdomains for use by your suppliers:

- `www-production.servicename.service.mygov.scot`
- `admin-production.servicename.service.mygov.scot`
- `assets-production.servicename.service.mygov.scot`

Your suppliers will use these subdomains to address your `www`, `admin` and `assets` services.

Detailed configuration advice for origin servers is outside of the scope of this document, but it's important to ensure that these 'origin domains' only listen for traffic from trusted sources like:

- the DDOS protection provider’s servers
- the locations where the service itself is being developed and/or managed

At present we advise against allowing DDOS protection suppliers to terminate SSL connections for transactional services carrying personal information, but this behaviour isn't prohibited at present. Although SSL termination on the third party network would allow the supplier(s) to carry out additional analysis and potentially extra mitigations against certain types of attack, it would also give the supplier access to all the personal information being submitted to your service.

There are obvious downsides to allowing this level of access, especially if the supplier’s network and processes have not been accredited to the same level as the rest of the service. It’s a risk-based decision, but if in doubt we suggest a presumption against SSL termination on third party networks.

Many suppliers offer IP forwarding DDOS protection, which does not have the same security issues as SSL termination, and is recommended in preference to SSL termination.  <mark>If your service requires transaction monitoring (which is not at all the same thing as DDOS protection) you should contact your CESG account manager for advice</mark>.

### Emails sent to service users

Emails to users of your service SHOULD be sent from a human-monitored email address that originates from the domain `servicename.service.mygov.scot` (and not the dept/agency or any other domain name).

You SHOULD enable [SPF](https://en.wikipedia.org/wiki/Sender_Policy_Framework) on the sending domain. You MAY also want to use [DKIM](http://www.dkim.org/) on the sending domain; it can provide additional guarantees about message authenticity and help recipients to more easily distinguish genuine mail from forgery.


## [Confidentiality](https://www.gov.uk/service-manual/domain-names/https.html)

Many services will collect personal information from users. It’s very important that this information can’t be intercepted by malicious third parties as it travels over the Internet.

Therefore, all services accessed through service.mygov.scot domains (including APIs) MUST only be accessible through secure connections. For web-based services this means HTTPS only (often referred to by the acronyms TLS or SSL, which both refer to the protocol underpinning these secure connections). Services MUST NOT accept HTTP connections under any circumstances.

### Subdomain names and certificates

When you are operating a service at servicename.service.mygov.scot, you will need testing and development environments. Given that these must use HTTPS, we suggest purchasing wildcard certificates with this naming convention:

- `*.preview.servicename.service.mygov.scot`
- `*.staging.servicename.service.mygov.scot`
- `*.servicename.service.mygov.scot`

The reasons why we prefer wildcard certificates include:

- being able to do HTTP 1.1 virtual hosting for HTTPS without relying on [Server Name Indication (SNI)](https://en.wikipedia.org/wiki/Server_Name_Indication). This is important because of legacy software which does not support SNI. It may not be possible to enumerate all of the names that will be served from a domain, so by allowing wildcards, we can meet that need. (You may have the public-facing www, admin and assets, but also non-public logging, monitoring and other services that still require TLS)
- having a different certificate for preview versus staging versus production means that we can potentially restrict who has access to the certificate. This is better from an operational security perspective. We should not use the same certificate on production as in development/test environments.

### Strict Transport Security

Strict Transport Security or HSTS is an extension to the HTTPS protocol that tells web browsers that they should make extra efforts to verify the security of a connection: they should assume for a specified period that all connections with this server should be via HTTPS and shouldn’t accept mixed content (where some content on a page is served via HTTPS and some via HTTP). This provides an extra level of assurance about the integrity of the connection.

Once a service manager has verified that their HTTPS setup is working fine they SHOULD enable [HSTS](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) on the production domains (www., admin. and assets.), by setting an HTTP response header such as

    Strict-Transport-Security: max-age=1209600, includeSubDomains;

representing a commitment to HTTPS-only traffic for 14 days. Once the service manager is confident that HSTS is configured correctly, you SHOULD increase the commitment to months or years:

    Strict-Transport-Security: max-age=31536000, includeSubDomains;

### Verification of SSL Certificates

In order to provide your service over HTTPS you will need to purchase a certificate (or certificates) from a recognised vendor. SSL vendors vary but regardless of which service you choose to use, you’ll need to validate with the vendor that you own the domain.

The verification methods that are commonly in use (in order of preference) are:

1. Create a file with a special code supplied by the SSL vendor on your website
2. Create a special DNS record with a code supplied by the SSL vendor
3. Sending an email to the owner of the service.mygov.scot domain

The least preferred method of sending an email to the domain owner relies on the DPS&BT Infrastructure Team seeing the verification email and responding. If this is necessary, then first send an email to the address that you intend to use for verification from your own email address warning that an SSL verification is needed for your service.

Your request should be sent to <mark>hostmaster@digital.cabinet-office.gov.uk</mark>, and should mention that an SSL verification email will be sent to them. It also helps if you include the domain name(s) to be secured and the name of the SSL certificate vendor.

The infrastructure team are unable to validate requests sent to any @service.mygov.scot address.

## Related

- [GDS on service subdomain names](https://www.gov.uk/service-manual/domain-names/service-subdomain-names.html)
- [GDS on managing domain names](https://www.gov.uk/service-manual/domain-names/how-they-work.html)
- [GDS on Domain Names, SSL, Email](https://www.gov.uk/service-manual/domain-names)
- [GDS on getting a domain name and start/end page](https://www.gov.uk/service-manual/domain-names/setting-up.html)

<!-- Acronyms -->

*[TLS]: Transport Layer Security
*[SSL]: Secure Socket Layer
*[SPF]: Sender Policy Framework
*[DKIM]: DomainKeys Identified Mail
*[APIs]: application programming interfaces
*[API]: application programming interface
*[DDOS]: Distributed Denial of Service
*[CDN]: Content Delivery Network
