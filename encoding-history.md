# History of the Burroughs Project Encoding Practices

*This document is meant to provide context for the changes made to the encoding since late 2015, when the project was taken on by Florida State University Libraries. We are providing an outline of the major changes, but have not included specific past iterations of the encoding documentation. If you would like information or documents (including previous versions of the encoded files) Contact either the digital humanities librarian or a member of Special Collections and Archives.*

## Early History

This project was originally started by Paul Ardoin as a part of his dissertation work. The work was done in collaboration with developers at the University of Antwerp. The infrastructure and encoding were based on the Samuel Beckett papers and adapted to the needs of Dr. Ardoin's research project.

In the early iterations of the project, witnesses were encoded and sent through several XSLT transformation pipelines, resulting in several versions of the same encoded text. Some were rich in styling and renditional information, others contained information about the collation of the text; some kept the witnesses separate and others collapsed all the witness information into one file.

Additionally, the files were structured using the TEI `<div>` and `<p>` elements (for "division" and "paragraph"). The documents used these elements to record each page, and the `<p>` was used as an arbitrary marker to make the files TEI compliant (you are not allowed to nest `<seg>` elements within `<div>` without some intermediary). 

## Transfer to FSU

FSU took on the Burroughs Project from Antwerp starting in 2015. This resulted in the development of a new interface for displaying the Burroughs documents. In order to create an interface that worked well with FSU's infrastructure (Islandora), library staff came up with new standards for encodign the documents. `<div>` elements were changed to `<surface>`; `<p>` was changed to `<zone`; `<seg>` was changed to `<s>` (for sentence).

Additionally, the mechanism for numbering sentences were changed to allow for a more streamlined way of displaying collations. Sentences, which had originally received a 3-digit number based on the published version of the text, now were given a 5-digit number (the original number, its position in the text; and a number indicating if it was linked to another sentence fragment).

Additionally, information on handwritten additions was streamlined. Instead of recording both the person who intervened and information about the ink they used, a standard for hands was developed that differentiated hands both by the actor intervening *and* the ink used. So where as additions were recorded as `<add rend="blueink" hand="#WSB">`, "WSB1" could be defined as "William Burroughs's hand in blue ink," and could thus be encoded as `<add hand="#WSB1">`. This reduced the amount of information needing to be processed by the stylesheets in publication.

These developments meant that, instead of having four publication pipelines, the documents could simply be encoded and all the necessary components of the ingest packages for publication should be produced in one phase.

The goal of the encoding changes was to record the information carried in multiple versions of the file and store them in only one version that could then generate all the necessary components for publication. It is our intent that these encoded files contained all the information that Paul Ardoin used for his dissertation and various publications, just with slightly different and updated vocabularies and information structure. If you would like to see the encoded files in their previous state (before the FSU transfer), please contact a member of the project team.