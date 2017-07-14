# Elements Used in the Burroughs Project

This is the reference encoding documentation for the Burroughs Project. For narrative instructions on how to transcribe and encode documents, see the [Encoding Narrative](encoding-narrative.md). For information on capturing metadata about the documents, see the section on the [TEI header](header.md)

## Table of Contents

1. Division-level features
  A. &lt;sourceDoc&gt;
  B. &lt;surfaceGrp&gt;
  C. &lt;surface&gt;
2. Chunk-level elements
  A. &lt;zone&gt;
  B. &lt;s&gt;
3. Phrase-level features
  A. &lt;subst&gt;
  B. &lt;add&gt;
  C. &lt;del&gt;
  D. &lt;metamark&gt;
  E. &lt;unclear&gt;
  F. &lt;gap&gt;
4. Hypertextual features
  A. &lt;anchor/&gt;
  B. &lt;note&gt;
  
## Division-level features

### &lt;sourceDoc&gt;

The `<sourceDoc>` element surrounds the entire text. If you are used to working with other TEI documents, this roughly corresponds with the `<text>` element. all of your transcribed text should go within `<sourceDoc>`.

`<sourceDoc>` should always be assigned an `@xml:id` that corresponds to the Special Collections naming conventions for the document. Generally, this will consist of the name of the text and a 5-character identifier for the witness. So, for example, the manuscript from FSU for the Blade Runner would be "bladerunner-msfsu."

### &lt;surfaceGrp&gt;

`<surfaceGrp>` groups together "surfaces" or pages. If you were to encode multiple documents within one xml file, you would group each document within its own `<surfaceGrp>`. As it stands, we encode one document per xml file, so you will only every have one `<surfaceGrp>` within each `<sourceDoc>`

### &lt;surface&gt;

The `<surface>` element corresponds to one side of a given page. Each `<surface>` should be assigned a `@facs` (facsimile) attribute that corresponds to the file name of the image for a given digitized page. If you do not know the file naming convention for `@facs` on a given document, do not add `@facs`, as a project manager or library staff person will add this during the publication process.

If a given page was originally hand-written, you should give the `<surface>` the `@ana` attribute with a value of "#manuscript". If it was typed, do not use `@ana`.

<!-- Include information about recto and verso pages + xml:ids -->

## Chunk-level elements

### &lt;zone&gt;

### &lt;s&gt;

## Phrase-level features

### &lt;subst&gt;

### &lt;add&gt;

### &lt;del&gt;

### &lt;metamark&gt;

### &lt;unclear&gt;

### &lt;gap&gt;

## Hypertextual features

### &lt;anchor/&gt;

### &lt;note&gt;

