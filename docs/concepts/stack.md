# The Islandora Software Stack

Islandora is "using Drupal as a repository." In order to provide various functions and services, it relies on a suite of many components working in unison. Islandora does not prescribe how a repository must function or make decisions, and as such virtually all components (except Drupal) are optional. The features below, which synchronize metadata to a Fedora repository and provide derivatives by microservices, are contained in the "out of the box" installations (such as the sandbox, Docker, and Ansible).

This page gives a basic overview of how the parts of Islandora work together. It includes a conceptual model (the Bento Box), an architecture diagram, and brief summaries of the tools used by Islandora. 

For more complete descriptions and installation instructions, see the manual installation section. `

# Islandora as a Bento Box

While previous versions of Islandora considered the stack as represented by a hamburger with ordered, layered toppings, Islandora components now interact like a metaphorical "bento box", where components are mostly separated and can be included, swapped, or removed as needed without disrupting the other parts of the stack. 


![Islandora 8 as a bento box](../assets/user-intro-bento.png)


# Islandora 8 Architecture Diagram

The following diagram was prepared by [Bethany Seeger](https://github.com/bseeger) based on work done by [Gavin Morris](https://github.com/g7morris). Components are listed below.
 
![Detailed diagram of the Islandora platform and its components](../assets/diagram.png)
 
 
## Components
 
### Support Stack

* [Apache](https://www.apache.org/) - The Apache HTTP Server, colloquially called Apache, is a free and open-source cross-platform web server software. Provides the environment in which Islandora 8 and its components run. Apache on Linux, along with PHP and MySQL (or similar) forms a LAMP stack and the basis for running Drupal.
* [MySQL](https://www.mysql.com/) - MySQL is an open-source relational database management system. Used as a Drupal database in Islandora 8, it can be easily replaced with other database management systems such as [PostgreSQL](https://www.postgresql.org/)
* [Drupal](https://www.drupal.org/) - Drupal is an open source content management system, and the heart of Islandora 8. All user and site-building aspects of Islandora 8 are experienced through Drupal as a graphical user interface.
* [Tomcat](http://tomcat.apache.org/) - an open-source implementation of the Java Servlet, JavaServer Pages, Java Expression Language and WebSocket technologies. Tomcat provides a "pure Java" HTTP web server environment in which Java code can run. Tomcat hosts FITS, Blazegraph, Cantaloupe, and Fedora.
* [Karaf](https://karaf.apache.org/) - A modular open source OSGi runtime environment. It hosts the connectors for microservices including the Fedora and Blazegraph indexers. 
* [ActiveMQ](https://activemq.apache.org/) - Apache ActiveMQ is an open source message broker written in Java together with a full Java Message Service client, which we use as a queue for messages so they can be processed at scale. 


### Islandora 
 
The following components are microservices developed and maintained by the Islandora community. They are bundled under [Islandora Crayfish](https://github.com/Islandora/Crayfish):
 
* [FITS](https://github.com/roblib/CrayFits) - A Symfony 4 Microservice to retrieve technical information from FITS and persist it as a Drupal media node. Works with [Islandora FITS](https://github.com/roblib/islandora_fits)
* [Gemini](https://github.com/Islandora/Crayfish/tree/dev/Gemini) - A path mapping service for Islandora 8.  Gemini links URLs of Drupal content with their URLs in Fedora.
* [Homarus](https://github.com/Islandora/Crayfish/tree/dev/Homarus) - Provides [FFmpeg](https://www.ffmpeg.org/) as a microservice for generating video and audio derivatives.
* [Houdini](https://github.com/Islandora/Crayfish/tree/dev/Houdini) - [ImageMagick](https://www.imagemagick.org/script/index.php) as a microservice for generating image-based derivatives, including thumbnails.
* [Hypercube](https://github.com/Islandora/Crayfish/tree/dev/Hypercube) - [Tesseract](https://github.com/tesseract-ocr) as a microservice for OCR.
* [Milliner](https://github.com/Islandora/Crayfish/tree/dev/Milliner) - A microservice that converts Drupal entities into Fedora resources.
* [Recast](https://github.com/Islandora/Crayfish/tree/dev/Recast) - A microservice that remaps Drupal URIs to add Fedora to Fedora links based on associated Drupal URIs in RDF.
 
 
### Other Open Source 
 
The following components are deployed with Islandora, but are developed and maintained by other open source projects:
 
* [Solr](https://lucene.apache.org/solr/) - An open-source enterprise-search platform. Solr is the default search and discover layer of Islandora 8, and a key component in some methods for [migration from Islandora 7 to 8](https://github.com/Islandora-devops/migrate_7x_claw) 
* [Blazegraph](https://blazegraph.com/) - Blazegraph is a triplestore and graph database.
* [Cantaloupe](https://cantaloupe-project.github.io/) - an open-source dynamic image server for on-demand generation of derivatives of high-resolution source images. Used in Islandora 8 to support [IIIF](https://iiif.io/)
* [Fedora](https://wiki.lyrasis.org/display/FF/Fedora+Repository+Home) - A robust, modular, open source repository system for the management and dissemination of digital content. The default smart storage for Islandora 8.
* [Matomo](https://matomo.org/) - Matomo, formerly Piwik, is a free and open source web analytics application. It provides usage statistics and a rich dashboard for Islandora 8.


 
