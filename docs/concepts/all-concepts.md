# Resource Nodes

Islandora has had the concept of "a digital object" as a basic unit of discussion. In Fedora 3 and before, this concept was structured by the Fedora Object Model paradigm, which instantiated many of these properties and things directly, and fedora objects could be discretely managed. It had:

- an identifier ("PID")
- properties (label, owner, date created, date modified)
- states (active, inactive, deleted)
- attached files called "datastreams" each with a string ID
	- metadata datastreams (often XML such as MODS or DC)
	- file datastreams (including original files, derivatives, etc.
- a non-editable audit log
- object-level privacy settings (which could applied to the whole object or individual datastreams).
- one or more "content models" or categories which caused the object to be interacted with in different ways.

Objects were stored in Fedora, but could be viewed (and edited, and managed) in Islandora at a URL based on the object's PID.

Objects could be related to other objects. For example, objects could be "a member of" a collection, or a compound object. Some compound objects, like newspaper issues, included an ordering of the children. We called these types "paged content." 

The object's type also determined what would happen to the attached files on ingest. For example, images would have smaller images created from them. We called these derivatives.


Concept: An Islandora Repository


Work in Progress. Topics to cover:

- What is a digital repository? A collection of resources.
- In Islandora does that mean that the Drupal website is the same as the repository? yes and no.
- Usually a repository is responsible for long-term preservation, management and/or curation, assigning metadata based on standards and using well-known vocabularies, and providing identifiers for items in the repository.
- All repositories are different, so Islandora makes it very configurable what is done and how.

In Islandora, all your Islandora (repository) content is Drupal content, but not all your Drupal content needs to be Islandora (repository) content. 

Items in a repository

Resources in a repository is vague, and encompasses any and all data/metadata. However in digital preservation we often think of a repository as containing discrete "items".

- an "item" in a repository can be anything, but usually involves some metadata and some files (digitized or born digital). Often we model an "item" in the repository after an "item" in the real world, such as a dissertation, a journal article, a photograph, a document, a newspaper issue, or a map. This usually, but does not have to, correspond to the concept of a "Work" in BIBFRAME and in FRBR. This "thing" can be digitally embodied in a file, multiple files, or no files. Sometimes its embodiment takes the form of a collection of items in the repository. 

Examples:

A map in a repository may be a high-resolution scan of a copy of a historical map (one file).
A document in a repository may be a born-digital report, made available simultaneously as a PDF and EPUB (multiple files).
A journal article citation may be in a repository, even if there is no full text available due to licensing issues (no files)
A newspaper issue in a repository may be a set of TIFFs, each containing the scan of a newspaper page. Depending on the repository's preference, each newspaper page may also be an 'item' in its own right (collection of other items)

In Islandora we use nodes to represent "items" and media to hold the files.


How content is modelled is very flexible. See  _Resource nodes_ for thte islandora construction of an object. See Islandora defaults for how islandora defaults configures it.

see also: metadata
see also: files



Concept: Repository Backend

Fedora sits behind Islandora as the repository filesystem and object information store. It provides preservation features like checksums. we put things in Fedora Because. Your files are there because good. Your metadata goes there as RDF. 
See also: How RDF gets into Fedora.

Concept: RDF Triplestore

while your rdf is in fedora and fedora acts as a LDP server, you may want to do queries and that's why triplestore. see Triplestore.

Concept: Derivative Microservices

We often want to make smaller versions of files from the ones we store. for scalability and to not impact the drupal server, we have microservices set up that do this. 

See more on: Crayfish.


Concept: Messaging service? middleware?

to coordinate the 






Fetaure: triplestore

we sync simultaneously to fedora, because fedora not great w rdf searching.

Feature: Fedora 
- part 1: how files get into fedora (flysystem)
- part 2: how metadata gets into Fedora


Contrib Modules: Flysystem

use alt filesystems. Used to put files into fedora. also used for S3.

Feature: S3
??






The objects in a repository may take many forms and represent many different real-world entities. 

DEVIATION: Media in Islandora

Concept: Membership

Concept: 

Concept: Collections or Concept: Organizing / complex Items

- we use a membership field. member_of.
- we use weights field_weight. Together, voila.

what is provided by drupal/islandora/defaults?


Feature: Collections

Collections use a membership field like member_of. tab?E@?! concept: collections in islandora defaults, 

expected behaviour:

- create a repository item that is tagged as a "collection" in field_model.
- Add members to the collection (members tab?) that are repository items. give them thumbnails or make thumbnails happen.
- on the collection, see a display of the "children"s thumbnails.

Components:
- a content type with field member_of
- a content type to be the collection (in this case, repository item plus model field option)
- a view that displays chidren of a given node
- a context to make that view show up on collections.


Feature: Paged Content


Concept: Derivatives
- use microservices
- 

Feature: thumbnails (defaults)
Feature: medium size (defaults)

expected behaviours:
- create a repo item, tag it with "image" (video, etc) 
- add a media of appropriate type (image or File) and tag it original file.
- publish the media.
-  wait a moment
- see new media in media tab.


Components:

- a microservice somewhere 
- a alpaca
- a queue
- a derivative action category
- a derivative action config
- 
- a content type to trigger 
- a context that causes "derivatives" actions to trigger
- an action object that is the particular configuration 



Concept: Metadata

DEVIATION: Fields in Islandora

Concept: Viewers

DEVIATION: Contexts in Islandora: 



Rube Goldberg Machine:
HOw rdf gets into fedora:
Motivation: 
we want to store info about our objects in fedora. Fedora takes RDF therefore our objects need to be described in RDF.
- this is one of several ways we do linked data. See linked data for more.
- 
Example from Islandora Defaults:

Components:
- RDF module 
- JSON-LD module
- RDF configurations (per content type, media type, taxo vocabulary)
- Context (with Islandora-created things)

Example 



HOW TO edit or add an RDF mapping
(like mark jordan's how-to guide, you know what you're doing but want some instruction)
