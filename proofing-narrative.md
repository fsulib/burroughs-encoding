# Procedures for Proofing Burroughs Project Documents

*This document outlines the procedures for proofing and checking the Burroughs documents in preparation for publication. It includes both the procedure for proofing to be conducted by the encoders and student workers for the project, as well as the publication workflows in the weeks leading up to ingest in DigiNole. The latter portion of this workflow should be completed by a project manager or library staff member.*

## Proofing procedures for encoders

Before the documents are loaded into the test proofing interface, you will need to proofread from the underlying XML. Once a document is finished being encoded, let the publication manager know, and they will print out a copy of the full XML file. From here, an encoder *who was not involved with the encoding of the text being proofed* will go through the XML file, compare it to the images of the original, and mark the changes in both the encoding and the transcription.

Once this process is complete, a third person *who was neither the encoder of the file, nor the proofreader* will go through and enter the appropriate changes into the XML file. If the proofreader and the corrections enterer disagree about an interpretation or a reading, it will be brought up in an encoding meeting, where the group will determine what the most likely correct reading is.

Once this process is complete, notify the publication manager, who will then generate the test proofing version to be checked in the rendered interface.

## Publication workflow for project managers and library staff

### Cleaning up systemic problems

If you have the <oXygen/> XML editor, you should use it to run some checks on the texts before you generate the stylesheets. The first thing to do is to create a new project that contains every witness that will be published in that round. You should then run some standard XPath searches on that project, using the XPath search bar in the top left corner of your <oXygen/> editor. 

The following are a few tests that should be run on the documents before they are transformed using the XSLT stylesheets:

```
//add[not(@place)]

//add[@type]

//del[@type]

//del[not(@rend)]

//subst[not(@hand)]
```

If any of these return any results, you should correct them. *The one exception to this rule, is if* `<del>` *has a* `@status` *of "shortEnd" or "shortStart"*. Look at the document to determine the value of `@place` for `<add>`. You should also record the information contained by `@type` on `<add>` and `<del>` to be within another allowable attribute. This will most likely be the `@place` attribute for `<add>` and the `@rend` attribute on `<del>`. Record the hand for `<subst>` based on the information in the [Known Hands](hands.md) document. For more information on the attributes used in the Burroughs documents, see the [Attributes List](attributes-list.md).

You should also test for instances where the `@hand` attribute is not recorded for `<del>` and `<add>`.This is a slightly tricker process, since there are several `<add>` and `<del>` elements do not have `@hand` attibutes because that information is recorded in `<subst>`. You need to look for the following XPaths:

`//add[not(parent::subst)][not(@hand)]`

`//del[not(parent::subst)][not(@hand)]`

If these return any results, add the correct information on `@hand`.

`//del/@status`

The only allowable value of `@type` on `<del>` is `implied` (although <oXygen/> may return some instances of `<del status="unremarkable">`, as that is the default value for that attribute; just make sure that these attributes are not actually typed in). 

#### Testing consistency

It is also a good idea to test the attribute values on as many elements as possible to ensure that no small typos or inconsistencies were introduced into the texts. You can do this with XPath's `distinct-values()`

In <oXygen/>, configure working sets to the text directory or project, and type the following into the XPath search window:

`distinct-values(//elementName/@attName)`

substituting "elementName" and "attName" with the relevant text. It's best to test `@place` on `<add>`, `@rend` on `<del>`, and `@hand` on `<add>`, `<del>` and `<subst>`. You should also check the various attributes on elements `<metamark>`, `<hi>`, `<unclear>`, etc.

### Proofing from the test interface

During the process of [creating ingest packages](publication-workflows.md), the project manager will also create full HTML files using full-html.xsl.

When you are proofing from these files, you should be checking the HTML files against the manuscript images, and looking for dropped words, incorrectly colored text, misaligned text, and unrendered/incorrectly-rendered text.

More specifically, you are checking that:

* deletions are marked as such
* additions appear in generally the right place (keeping in mind that most additions are superscripts, unless they appear as marginal additions)
* Metamarks such as connecting lines, inserting carrots, and arrows appear
* Text is generally colored in a way that corresponds to the ink colors you see on the page (i.e. blue pen appears as blue text in the interface).

If you see any errors in rendering or in text being incorrectly displayed, first check the XML file to see if the error appears in the encoding. If so, make the change directly in the encoded file. If the error is a systemic display problem (i.e. the error is a result of the stylesheet process and does not appear in the encoded document), make a note of it in a separate document for the project manager. If you see a systemic display error, you do not need to mark it every time it appears unless the error manifests differently each time.

Once you have entered all the corrections in the XML file, you should notify the publications manager that proofing is complete, and that the document is ready for final publication review. At this time, you should also send along any systemic styling errors that you noted during the test proofing phase.

