# Best practices for encoders 

## Keep your XML readable

For the sake of future proofreaders, you will want to make sure that your XML files are relatively readable and navigable. To aid with this you should follow the following rules as best as possible:

1. **Keep your tabs in sync with the nested structure** - Instead of keeping all of your lines all the way on the left side of the page, try to tab in for each time you nest an element, up through `<zone>`. &lt;oXygen/&gt; does this natively. Basically, this means indenting when you have an element that occurs *inside* another.
2. **Line up your &lt;lb&gt;s** - Do a carriage return every time there's a new line in the text your transcribing, and line up the `<lb/>` (line begins) elements with each other. This will help the proofreader keep track of which line they are on.
3. **Put the &lt;lb/&gt; first** - If you encounter a sentence that begins on a new line, don't put the `<lb/>` tag *inside* the `<s>`; rather, put the `<lb/>` *outside* the `<s>` as the first thing on the new line.

All in all, your files should look something like this:

```
<sourceDoc>
  <surfaceGrp>
    <surface>
      <zone>
        <s>Some text here, and eventually theres a line
        <lb/><subst><del rend="crossOut">break</del><add place="inline">begins</add></subst>.<s>
        <lb/><s>You don't need to enter and indent text from phrase-level elements.</s>
        <lb/><s>Also notice that I put the <gi>lb</gi> element <emph>before</emph> the beginning
        <lb/>of the new <gi>s</gi> element.</s> <s>This increases readability.</s>
      </zone>
      <zone>
        <s>Keeping your XML somewhat organized and formatted will help future encoders
        <lb/>more easily understand and navigate your document.</s> <s>It also helps the 
        <lb/>publication manager as they go through the publication and transformation
        <lb/>processes.</s>
      </zone>
    </surface>
  </surfaceGrp>
<sourceDoc>
```

## Check well-formedness often

Before you save your document, you should always check the well-formedness. If you're using &lt;oXygen/&gt;, you will frequently use the validation features that tell you whether your document is compliant with the rules laid out in the schema. However, sometimes your document will not fit perfectly into the rules that the schema applies. And that's okay! You can still commit your documents when they aren't perfectly valid. *However*, you should **always** make sure that your documents are well-formed (i.e. compliant with the larger rules of XML). The publication manager and library staff cannot check for problems with your document (or even process your document), if it is not well formed.

To check well-formedness in &gt;oXygen/&lt;, find the "Validate" button (it looks like a piece of paper with a red check mark superimposed on top of it). Click on the dropdown arrow/triangle to the immediate right of this button. This should bring up a few different options. Now click on the "check well-formedness" option (blue checkmark superimposed over a piece of paper), and make sure that it returns the message "Document is well-formed." If it is, then feel free to go on your merry way. If it is not *do not commit to the version management system*. Find where the document is having problems, and correct it, before committing changes. If you cannot find where the error is, contact the publications manager or digital humanities librarian.