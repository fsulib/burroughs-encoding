# Procedures for Proofing Burroughs Project Documents

This document outlines the procedures for proofing and checking the Burroughs documents in preparation for publication. It includes both the procedure for proofing to be conducted by the encoders and student workers for the project, as well as the publication workflows in the weeks leading up to ingest in DigiNole. The latter portion of this workflow should be completed by a project manager or library staff member.

## Proofing procedures for encoders

*This section will be written at a later date.*

## Publication workflow for project managers and library staff

### Cleaning up systemic problems

If you have the &lt;oXygen/&gt; XML editor, you should use it to run some checks on the texts before you generate the stylesheets. The first thing to do is to create a new project that contains every witness that will be published in that round. You should then run some standard XPath searches on that project, using the XPath search bar in the top left corner of your &lt;oXygen/&gt; editor. 

The following are a few tests that should be run on the documents before they are transformed using the XSLT stylesheets:

`//add[not(@place)]`

`//add[@type]`

`//del[@type]`

`//subst[not(@hand)]`

If either of these return any results, you should correct them. Look at the document to determine the value of `@place` for `<add>`. You should also record the information contained by `@type` on `<add>` and `<del>` to be within another allowable attribute. This will most likely be the `@place` attribute for `<add>` and the `@rend` attribute on `<del>`. Record the hand for `<subst>` based on the information in the [Known Hands](hands.md) document. For more information on the attributes used in the Burroughs documents, see the [Attributes List](attributes-list.md).

You should also test for instances where the `@hand` attribute is not recorded for `<del>` and `<add>`.This is a slightly tricker process, since there are several `<add>` and `<del>` elements do not have `@hand` attibutes because that information is recorded in `<subst>`. You need to look for the following XPaths:

`//add[not(parent::subst)][not(@hand)]`

`//del[not(parent::subst)][not(@hand)]`

If these return any results, add the correct information on `@hand`.

`//del/@status`

The only allowable value of `@type` on `<del>` is `implied` (although &lt;oXygen/&gt; may return some instances of `<del status="unremarkable">`, as that is the default value for that attribute; just make sure that these attributes are not actually typed in). 