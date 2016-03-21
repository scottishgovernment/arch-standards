# Catalogue of Provisional Industry Standards


## Purpose

This catalogue lists industry standards related to the delivery of digital services in Scotland. Standards will be added, updated and removed over time in order to reflect the changing landscape of digital delivery.

Standards in this catalogue will be endorsed based on the standards endorsement process defined in our architecture metamodel.


## Contents

<!--TOC max3-->


## Revision History

| Version       | Issued     | Comments
| -             | -          | -
|           0.1 | 11-08-2015 | Created and added an entries for HTML & CSS.
|           0.2 | 28-08-2015 | Corrected purpose section.


## Standards

### [HTML 5](http://www.w3.org/TR/html5/single-page.html)

> HTML5 is a core technology markup language of the Internet used for structuring and presenting content for the World Wide Web. It is the fifth revision of the HTML standard (created in 1990 and standardised as HTML 4 as of 1997) and, as of December 2012, is a candidate recommendation of the World Wide Web Consortium (W3C). Its core aims have been to improve the language with support for the latest multimedia while keeping it easily readable by humans and consistently understood by computers and devices (web browsers, parsers, etc.). HTML5 is intended to subsume not only HTML 4, but also XHTML 1 and DOM Level 2 HTML. ~[Wikipedia](http://en.wikipedia.org/wiki/HTML5)~

Citizens and businesses must be able to access public sector information online. Access to these documents should be both simple and convenient. This means that viewing such documents should not require the installation of an app or plugin, should not require the purchase of specialist software and should not impede the use of accessibility tools such as screen readers.

HTML is ubiquitous as a format for transmitting and viewing documents on the internet. It enjoys support across nearly all consumer devices that can be connected to the internet. HTML5 is the latest revision of the HTML standard and represents a significant body of changes to reflect the evolving use of the web as a platform to deliver both information and transactional services. The HTML5 standard has now now been endorsed by its advisory committee and published by the W3C as a standard. Browser support for HTML5 features in the UK is [now between 90 and 95%](http://caniuse.com) and, as such, it should be considered the default choice for authoring documents on the web.

We expect the use of HTML5 to deliver the following benefits in terms of digital delivery:

- The HTML5 standard includes native support for audio and video streams. Previously the delivery of multimedia in a browser often required the installation of third-party plugins. Use of HTML5 multimedia will make it more convenient and reliable to access such content while maintaining compatibility across both desktop and mobile browsers;
- HTML5 includes an extend set of semantic tags for representing content. This will allow user agents to make intelligent decisions about the handling of content improving both accessibility (via screen readers) and findability (search engines);
- HTML5 includes a suite of capabilities including canvas, drag'n'drop and editable content elements that will allow enhancements related to on page interactivity (however, care should be taken to maintain accessibility);
- HTML5 includes features such as local storage that allow web sites and applications to handle low or zero bandwidth use cases. This will allow improvements to the user experience for mobile particularly in areas of poor connectivity;
- HTML5 includes a geolocation capability that will allow service providers both to provide more accurate information as well as to personalise web pages and web applications.

HTML is a general purpose standard that can be used to deliver content for display across a range of devices including desktop browsers, mobile browsers and printers.

| -                  | -                               |
| Standards Body     | [W3C](http://www.w3.org)        |
| Endorsement Status | Provisional Standard               |
| Applicability      | Data Standard                   |
| Open Standard?     | Expected Yes[^expect-yes]       |
| License            | [W3C Document Licence][w3c-lic] |

### [CSS 3](http://www.w3.org/Style/CSS/current-work.en.html)

> Cascading Style Sheets (CSS) is a style sheet language used for describing the look and formatting of a document written in a markup language. While most often used to change the style web pages and user interfaces written in HTML and XHTML, the language can be applied to any kind of XML document, including plain XML, SVG and XUL. CSS is a cornerstone specification of the web, and almost all web pages use CSS style sheets to describe their presentation. ~[Wikipedia](http://en.wikipedia.org/wiki/Cascading_Style_Sheets)~

We expect the use of CSS to deliver the following benefits in terms of digital delivery:

- One of the primary features of CSS is that it allows the separation of concerns when build web sites and web applications. HTML documents can be used to represent the web content and CSS can be used to lay out and style the content. Separating content from its layout very often provides a maintainability benefit as the content and styling can now be evolved independently, and potentially in parallel;
- Separating styling from content also allows the same styles to be re-used across multiple related sites or applications;
- CSS provides features such as media queries which can be used to changing styling for different devices or to target specific styles to a single class of devices. This simplifies the delivery of a web site or web application across multiple channels (e.g. desktop, mobile, TV);
- CSS includes features that allow the styling of web pages when they are printed allowing the support of some offline / assisted digital use cases;
- CSS includes features that allow specific capabilities of browsers to be detected. This provides benefits from an application compatibility perspective as it simplifies the progressive enhancement and/or graceful degradation of web pages;
- Separating style from content allows styles to be cached by a browser rather than being resent with every web page request. This can provide a significant performance improvement for web sites and applications and is particular beneficial when delivering services to mobile devices that operate with limited bandwidth;
- Separating content from style increases the likelihood that software such as screen readers will correctly interpret web pages leading to an increase in the accessibility of the web site or web application;
Separating content from style increases the likelihood that search engines will correctly interpret the web page improving search rankings and increasing the likelihood that potential users of the service will find it.

CSS is a general purpose standard that can be used for styling HTML & XML documents for display across a range of devices including desktop browsers, mobile browsers and printers.

| -                  | -                               |
| Standards Body     | [W3C](http://www.w3.org)        |
| Endorsement Status | Provisional Standard               |
| Applicability      | Data Standard                   |
| Open Standard?     | Expected Yes[^expect-yes]       |
| License            | [W3C Document Licence][w3c-lic] |


### [Atom Syndication Format](https://tools.ietf.org/html/rfc4287)

The Atom Syndication Format (commonly referred to as simply 'Atom') is an XML-based hypermedia format. Where as HTML focuses on the representation of documents as hypermedia, Atom can be used to represent lists of content items along with supporting metadata. The idiomatic use of Atom is to represent a time-based list of content items such as blog posts or news articles. However, Atom is flexible and extensible enough to be used as a general purpose tool for the interoperable transfer of data between applications.

Benefits of using the Atom format:

- Atom supports 'media-type composition' allowing clear separation of the business content from structural and metadata elements of a document. This separation of concerns enhances the interoperability and modifiability of systems as the transport and processing of events can be evolved independently.
- Separation of concerns also allows for the creation of domain agnostic applications to be created to support use cases such as operational monitoring, debugging and message creation.
- The Atom format is well supported across the majority of popular programming languages (including Java, C# & Ruby) reducing the effort required when integrating solution components.
- The Atom format is designed to handle offline and limited connectivity use cases as well as to work in synergy with other key web standards such as HTTP. This allows the efficient implementation of features such as document caching that can simplify the delivery of a system's availability and resilience requriements.
- The Atom format is designed to provide a variety of extension points (including both metadata and content extensibility) allowing for flexibility of use across a broad variety of problem domains.

Typical use cases for the Atom format:

- **Modelling a list of resources**: Atom can be used as a data standard to describe a collection of ordered resources (along with associated metadata) such as search results or news articles.
- **Syndicating content**: Atom can be used in conjuction with an appropriate publishing protocol in order to syndicate data across a network of clients.
- **Augmenting data standards with metadata**: where an existing (and possibly proprietary) data standard exists to describe domain resources this can be wrapped into an Atom entry in order to associate data related to the resource's lifecycle.
- **Integrating event-driven systems**: Atom enables the implementation of vendor-agnostic, asynchronous messaging. In architectures where it is acceptable to trade scalability for latency Atom can be used as the substrate for 'publish subscribe' style integration of applications or services.

Use of Atom should be preferred over use of RSS. See this linked [comparison of RSS 2.0 and Atom 1.0](http://www.intertwingly.net/wiki/pie/Rss20AndAtom10Compared) for more details.

| -                  | -                               |
| Standards Body     | [IETF](https://www.ietf.org)    |
| Endorsement Status | Provisional Standard            |
| Applicability      | Data Standard                   |
| Open Standard?     | Unknown[^unknown]               |
| License            | Unknown                         |


## Appendices

### Standards Lifecycle

*The following is an extract from the TOGAF standard version 9.1 and describes the endorsement statuses used in the preceding sections.*
Standards do not generally exist for all time. New standards are identified and managed through a lifecycle process. Typically, standards pass through the following stages:
- **Proposed Standard**: A potential standard has been identified for the organisation, but has not yet been evaluated for adoption.- **Provisional Standard** (also known as a Trial Standard): A Provisional Standard has been identified as a potential standard for the organisation, but has not been tried and tested to a level where its value is fully understood. Projects wishing to adopt Provisional Standards may do so, but under specific pilot conditions, so that the viability of the standard can be examined in more detail.- **Standard** (also known as an Active Standard): A Standard defines a mainstream solution that should generally be used as the approach of choice.- **Phasing-Out Standard** (also known as a Deprecated Standard): A Phasing-Out Standard is approaching the end of its useful lifecycle. Projects that are re-using existing components can generally continue to make use of Phasing-Out Standards. Deployment of new instances of the Phasing-Out Standard are generally discouraged.- **Retired Standard** (also known as an Obsolete Standard): An Retired Standard is no longer accepted as valid within the landscape. In most cases, remedial action should be taken to remove the Retired Standard from the landscape. Change activity on a Retired Standard should only be accepted as a part of an overall decommissioning plan.All standards should be periodically reviewed to ensure that they sit within the right stage of the standards lifecycle. As a part of standards lifecycle management, the impact of changing the lifecycle status should be addressed to understand the landscape impact of a standards change and plan for appropriate action to address it.

### Standards Applicability

Standards within a standards information base are typically classified according to their applicability. For the purpose of the standards catalogue we will re-use the TOGAF definitions as follows:

- **Business Standards**:    - Standard shared business functions;
    - Standard role and actor definitions;
    - Security and governance standards for business activity;- **Data Standards**:    - Standard coding and values for data;    - Standard structures and formats for data;
    - Standards for origin and ownership of data;
    - Restrictions on replication and access;- **Applications Standards**:    - Standard/shared applications supporting specific business functions;
    - Standards for application communication and interoperation;    - Standards for access, presentation, and style;- **Technology Standards**:    - Standard hardware products;    - Standard software products;    - Standards for software development.


## Glossary

Hypermedia
: Hypermedia, is a nonlinear medium of information which can include graphics, audio, video, plain text and hyperlinks. This contrasts with the broader term multimedia, which may include non-interactive linear presentations as well as hypermedia. The World Wide Web is a classic example of hypermedia, whereas a non-interactive cinema presentation is an example of standard multimedia due to the absence of hyperlinks. (source: [Wikipedia](https://en.wikipedia.org/wiki/Hypermedia))

Hypermedia Format
: A hypermedia format is a data standard that can natively support the delivery of hypermedia. In practice, the key element here is that the standard has support for hyperlinks. Examples of hypermedia formats include HTML and Atom syndication format.

<!-- Footnotes -->

[^expect-yes]: Assuming that creation of this standard has followed the body's documented process we expect this to be considered an open standard.
[^unknown]: This standard has not been evaluated to determine if it is an open standard.

<!-- Links -->

[w3c-lic]: http://www.w3.org/Consortium/Legal/2015/doc-license
