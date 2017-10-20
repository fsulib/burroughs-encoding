# Encoding Narrative for the Burroughs Archive

## Encoding in XML 

As an encoder for the Burroughs Archive, you will be transcribing and encoding various drafts and witnesses of the work of William Burroughs in XML. For an introduction to the structure and logic of XML, read through the Text Encoding Initiative (TEI) Consortium's [A Gentle Introduction to XML](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/SG.html).

The Burroughs Archive uses a specific customization of TEI. That is to say, we follow most of the suggestions outlined in the various TEI specifications, but we disallow certain things that the TEI allows, and we have some additional rules that the TEI does not follow. You should utilize the documentation found in this repository to understand the encoding procedures, but you may supplement your knowledge by looking up some of the features in our documents in the wider [TEI Guidelines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/index.html) (specifically Appendices C and D).

If you encounter a feature in your documents that does not occur in the Burroughs-specific documentation, you can use the TEI Guidelines to find the appropriate element or attribute to describe the feature you encounter. However, if you decide to use it in a document, *you must bring it up at an encoding meeting or have a conversation with the publications manager*. This way, we can verify as a group that this feature is being encoded in the best way, and we can add the new encoding standard to our documentation and schemas, so that future encoders can know what to do if they encounter the same problem.

## How we think about text 

At the Burroughs Archive project, we think about the text as being divided up by physical pages rather than logical divisions. This essentially means that we care less about structural features (like chapters, scenes, paragraphs, etc.) and more about physical features (like sides of pages (surfaces), pasted down fragments, attachments, etc.).

Encoding physical features can often be a problem when you need to also address the semantic information in the text. For example, sentences often cross pages, words cross lines, and handwritten additions are scribbled at right angles in margins. That sometimes means we need to get creative about how we convey both physical and semantic interpretations of the text. To learn more about this, you should read about how we encode [rendition](attributes-list.md#rend) and (linking)[#attributes-list.md#part]

## Transcription 

Transcription of the Burroughs Texts is usually quite straightforward, as the documents are mostly typewritten with only some handwritten additions. This usually means that the text is somewhat consistent and legible, as compared to manuscripts. However, if you do encounter illegible text, make liberal use of the [&lt;unclear&gt;](elements-list#unclear) and [&lt;gap/&gt;](elements-list#gap) elements to indicate your uncertainty.

Most characters that you need to encode will be easily accessible via your keyboard. However, occasionally, you will encounter special characters that you cannot easily type. In this case, you will need to use entity references. These are strings that refer to other characters (they will display as these characters in the publication interface).

Entity references are specified in XML by using an ampersand to start and a colon to end. *This means that ampersands are special characters, and that you must use an entity reference to enter an ampersand*. If you need to transcribe an ampersand, you should use `&amp;`. 

Other common characters include:

| Character Name       | Character| Reference  |
|----------------------|:--------:|:----------:|
| en-dash              | –        | `&#x2013;` |
| em-dash              | —        | `&#x2014;` |
| superdash            | ―        | `&#x2015;` |
| left-pointing arrow  | ←        | `&#x2190;` |
| right-pointing arrow | →        | `&#x2192;` |
| pilcrow              | ¶        | `&#x00b6;` |



