# Elements Used in the Burroughs Project

This is the reference encoding documentation for the Burroughs Project. For narrative instructions on how to transcribe and encode documents, see the [Encoding Narrative](encoding-narrative.md). For information on capturing metadata about the documents, see the section on the [TEI header](header.md)

## Table of Contents

1. Division-level features
  A. <sourceDoc>
  B. <surfaceGrp>
  C. <surface>
2. Chunk-level elements
  A. <zone>
  B. <s>
3. Phrase-level features
  A. <subst>
  B. <add>
  C. <del>
  D. <metamark>
  E. <unclear>
  F. <gap>
4. Hypertextual features
  A. <anchor/>
  B. <note>
  
## Division-level features

### <sourceDoc>

The `<sourceDoc>` element surrounds the entire text. If you are used to working with other TEI documents, this roughly corresponds with the `<text>` element. all of your transcribed text should go within `<sourceDoc>`.

`<sourceDoc>` should always be assigned an `@xml:id` that corresponds to the Special Collections naming conventions for the document. Generally, this will consist of the name of the text and a 5-character identifier for the witness. So, for example, the manuscript from FSU for the Blade Runner would be "bladerunner-msfsu."

### <surfaceGrp>

`<surfaceGrp>` groups together "surfaces" or pages. If you were to encode multiple documents within one xml file, you would group each document within its own `<surfaceGrp>`. As it stands, we encode one document per xml file, so you will only every have one `<surfaceGrp>` within each `<sourceDoc>`

### <surface>

The `<surface>` element corresponds to one side of a given page. Each `<surface>` should be assigned a `@facs` (facsimile) attribute that corresponds to the file name of the image for a given digitized page. If you do not know the file naming convention for `@facs` on a given document, do not add `@facs`, as a project manager or library staff person will add this during the publication process.

If a given page was originally hand-written, you should give the `<surface>` the `@ana` attribute with a value of "#manuscript". If it was typed, do not use `@ana`.

<!-- Include information about recto and verso pages + xml:ids -->

## Chunk-level elements

### <zone>

These mark zones on the page. Generally, Burroughs's pages only consist of one zone, as he tends to write each page in one setting and oriented in the same direction. Occasionally, you will find text that is oriented sideways or upside down. This should be contained within a separate `<zone>` element.

### <s>

This element is used for each sentence-like element. Most of the `<s>` elements you encounter will be based off of the sentences that end up in the final published version. This basically means that you will ocassionally see sentences split into two `<s>` elements or two sentences collapsed into one `<s>`, as this structure reflects the finalized sentence structure in the later drafts. Most `<s>` elements will have an `@n` attribute that represents the sentence number as assigned by an encoder. You will also see an additional two numbers (each separated by a period). The first represents when a sentence occurs more than one time in a document (i.e. the first instance receives has a number of 000.1.0, whereas the second instance is 000.2.0; sentences that have no duplicates only have a "0" in this second place). The third number represents instances where the sentence is split across a page or other structure, such that the element needs to be split and rejoined during the indexing process. So, for example, a split sentence would have the number 000.0.1 and 000.0.2. You will need to use the `@next` and `@prev` elements to indicate that these elements should be joined together. 

## Phrase-level features

### <subst>

The `<subst>` element groups an <add> and a <del> element to indicate that the change consitutes a substitution. `<subst>` should always have a `@hand` attribute to indicate who made the substitution.

### <add>

The `<add>` element is used to indicate additions to the text. These may be instant additions, such as instances, where the typist typed over letters, or these could be handwritten additions made later in pen or pencil. `<add>` should always have `@place` element to indicate where on the written page the addition occurs. 

### <del>

### <metamark>

### <unclear>

### <gap>

## Hypertextual features

### <anchor/>

### <note>

