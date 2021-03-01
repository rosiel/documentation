# Resources: Nodes, Media, Files

In order to store the metadata and data together of a digital object, Islandora has the concept of a "Resource Node". 

A "Resource Node" is a Drupal Node that holds metadata about an object, with the digital content (if applicable) of that object stored in Drupal Media which are linked to that Resource Node. 

[Diagram of a Resource Node, a Media object, and a file. The file is stored in the Media object, and the Media object is "Media of" the Node.]

## Resources in Fedora

Using Fedora as a preservation layer has long been part of Islandora's mission. Since Fedora 4, content is created in Islandora as Drupal content, and the Drupal content can be automatically (based on some trigger using Contexts) synced to Fedora. In the case of using Media to store files, the Default configuration is such that all uploaded files go to and are stored in Fedora.

## Resource Nodes, Media, and Files vs Drupal Nodes, Media, and Files

Islandora does not constrain how data is set up, or how nodes, media, and files are used together. However, we ship with the following as defaults:

- a special content type ("Repository Item") meant to represent all nodes that are "in the repository" as opposed to Drupal site-building nodes
- media which hold singe files, those files (when uploaded using the GUI) being stored in Fedora (note: it is not possible with the default configuration to upload files to the Drupal file system unless changes are made to the configuration)
- contexts which cause drupal metadata to be sent to Fedora, which cause derivatives to be generated based on metadata at the node and media level, and which change the display features of the nodes and media. 


