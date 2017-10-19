# Elements Used in the Burroughs Project

This is the reference encoding documentation for the Burroughs Project. For narrative instructions on how to transcribe and encode documents, see the [Encoding Narrative](encoding-narrative.md). For information on capturing metadata about the documents, see the section on the [TEI header](header.md)

## Table of Contents

1. Division-level features
  1. &lt;sourceDoc&gt;
  2. &lt;surfaceGrp&gt;
  3. &lt;surface&gt;
2. Chunk-level elements
  1. &lt;zone&gt;
  2. &lt;s&gt;
3. Phrase-level features
  1. &lt;subst&gt;
  2. &lt;add&gt;
  3. &lt;del&gt;
  4. &lt;metamark&gt;
  5. &lt;unclear&gt;
  6. &lt;gap&gt;
4. Hypertextual features
  1. &lt;anchor/&gt;
  2. &lt;note&gt;
  
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

These mark zones on the page. Generally, Burroughs's pages only consist of one zone, as he tends to write each page in one setting and oriented in the same direction. Occasionally, you will find text that is oriented sideways or upside down. This should be contained within a separate `<zone>` element.

### &lt;s&gt;

This element is used for each sentence-like element. Most of the `<s>` elements you encounter will be based off of the sentences that end up in the final published version. This basically means that you will ocassionally see sentences split into two `<s>` elements or two sentences collapsed into one `<s>`, as this structure reflects the finalized sentence structure in the later drafts. Most `<s>` elements will have an `@n` attribute that represents the sentence number as assigned by an encoder. You will also see an additional two numbers (each separated by a period). The first represents when a sentence occurs more than one time in a document (i.e. the first instance receives has a number of 000.1.0, whereas the second instance is 000.2.0; sentences that have no duplicates only have a "0" in this second place). The third number represents instances where the sentence is split across a page or other structure, such that the element needs to be split and rejoined during the indexing process. So, for example, a split sentence would have the number 000.0.1 and 000.0.2. You will need to use the `@next` and `@prev` elements to indicate that these elements should be joined together. 

## Phrase-level features

### &lt;subst&gt;

The `<subst>` element groups an &lt;add&gt; and a &lt;del&gt; element to indicate that the change consitutes a substitution. `<subst>` should always have a `@hand` attribute to indicate who made the substitution.

### &lt;add&gt;

The `<add>` element is used to indicate additions to the text. These may be instant additions, such as instances, where the typist typed over letters, or these could be handwritten additions made later in pen or pencil. `<add>` should always have `@place` element to indicate where on the written page the addition occurs. 

### &lt;del&gt;

The `<del>` element is used to indicate text that was deleted. Deletions are created a number of ways in the Burroughs texts. The types of deletions are indicated with the `@rend` attribute. The possible values are:

1. erased - for cases where the text was erased with some type of typewriting instant-correction tape/fluid
2. crossedOut - for instances where the text was either crossed or scribbled out with a pen or overtyped with symbols, like "$" or "#". **Note that this is different than "overtyped" which is used with `<del>` in `<subst>` to indicate that the addition is typed over the deletion.**
3. overtyped - this is used only in `<subst>` to indicate that the addition was typed in over the original text.
4. overwritten - this is used only in `<subst>` to indicate that the addition was written in pen or pencil over the original text.

### &lt;metamark&gt;

This indicates some sort of editorial marker (often ones that cannot be represented by a character typed into the encoded document). These include arrows, carrots, connecting arcs to show deletions of spaces between words, etc.

`<metamark>` will usually not take any attributes. However, if the metamark is being used to indicate an insertion, `<metamark function="insert">` should be used. `@rend` should only be used on `<metamark>` if the metamark is used to indicate that characters should be "closed up" (i.e. the space or characters in between should be removed). For this type of editorial mark, you `@rend` should take the values of `upconnect` (for close-up marks that only occur above the letters), `downconnect` (for close-up marks that only occur below the letters), and `updownconnect` (for close-up marks that occur above and below the letters).

### &lt;unclear&gt;

This element is used to encode words and letters that cannot be easily read or whose readings are uncertain because of illegibility. `<unclear>` should always have an `@reason` attribute which indicates why the text is unclear. The values on reason are:

1. `poorlyInked` - This is used for typed letters and words that are unclear either because the ink was not properly applied to the page. This could happen because the typing mechanism was not properly depressed, or for some other reason. 
2. `illegible` - This is used for instances where text (almost always handwritten) is illegible because the letters are irregularly formed (or in some cases not formed at all).
3. `obscured` - This is used in cases where the text has been obscured by other writing, such as overwritten, overtyped, or crossed out text.
4. `damaged` - This is used in instances where the physical documents themselves are damaged.
5. `flawedReproduction` - In cases where you are working from a facsimile or digitized edition, you may end up using "flawedReproduction" (*although this is extremely rare*). This would be used in cases where you are confident that the illegibility is a result of an issue with the digitization or reproduction rather than the physical document itself. With documents transcribed from FSU's collections, you should try to check with the physical copy itself. Ideally, this value will never be used in cases where the encoder has access to the physical documents.

### &lt;gap&gt;

This element is used when the text is completely illegible. You should use the `@extent` attribute to indicate the number of characters that you think are illegible. If multiple lines are illegible, you should use a different `<gap>` element for each line, separating the lines with an `<lb/>` element.

## Hypertextual features

### &lt;anchor/&gt;

`<anchor/>` is an empty element used to mark where a `<note>` falls within the text. If an editorial note is commenting on a given word or section, you should put the anchor where the "\*" will appear in the published text. Each anchor should receive a `@corresp` attribute that points to the `@xml:id` of the `<note>` for that section.

### &lt;note&gt;

The `<note>` element contains the editorial note that comments upon a given section. `<note>` should always have a unique `@xml:id`. The numbering convention for the `@xml:id` on note is usually "n" followd by 3 digits. Notes should be ordered from the start to the end of the text. So, for example, the first note would be "n001", the second "n002", the third "n003", and so on.

