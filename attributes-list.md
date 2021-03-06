# Attributes Used in the Burroughs Project

This is the reference encoding documentation for the Burroughs Project. For narrative instructions on how to transcribe and encode documents, see the [Encoding Narrative](encoding-narrative.md). For information on capturing metadata about the documents, see the section on the [TEI header](header.md)

List of attributes and their allowed values

1. [@corresp](#corresp)
    1. [&lt;anchor/&gt;](#anchor)
2. [@extent](#extent)
    1. [&lt;gap/&gt;](#gap)
3. [@facs](#facs)
    1. [&lt;surface&gt;](#surface)
4. [@function](#function)
    1. [&lt;metamark&gt;](#metamark)
5. [@hand](#hand)
    1. [&lt;add&gt;](#add)
    2. [&lt;del&gt;](#del)
    3. [&lt;subst&gt;](#subst)
6. [@n][#n]
    1. [&lt;s&gt;](#s)
    2. [&lt;surface&gt;](#surface-1)
7. [@part](#part)
    1. [&lt;s&gt;](#s-1)
8. [@place](#place)
    1. [&lt;add&gt;](#add-1)
    2. [&lt;fw&gt;](#fw)
9. [@reason](#reason)
    1. [&lt;unclear&gt;](#unclear)
10. [@rend](#rend)
    1. [&lt;del&gt;](#del-1)
    2. [&lt;hi&gt;](#hi)
    3. [&lt;s&gt;](#s-2)
    4. [&lt;surface&gt;](#surface-2)
11. [@status](#status)
    1. [&lt;del&gt;](#del-2)
12. [@type](#type)
    1. [&lt;fw&gt;](#fw-1)
    2. [&lt;seg&gt;](#seg)
    3. [&lt;zone&gt;](#zone)
13. [@xml:id](#xmlid)
    1. [&lt;note&gt;](#note)
    2. [&lt;surface&gt;](#surface-3)

## `@corresp`

The `@corresp` attribute is used to show when one element corresponds to another. It contains any Uniform Resource Identifier (URI), which is usually just a pointer to another location in the document (i.e. an `@xml:id`).  

### `<anchor/>`

`<anchor/>` is the only element that takes `@corresp` as an attribute. The value of `@corresp` should be a pointer to the `<note>` element that glosses that specific section of text. Remember to always use a "#" before the string of the pointer.

#### Example
```
<anchor corresp="#n011"/> 
<note xml:id="n011">This portion of the text is upside down due to a false start.</note>
``` 

## `@extent`

The `@extent` attribute is used to record the length or span of a given feature. In the Burroughs documents, the `@extent` attribute is only used on `<gap>` to indicate how many characters are missing.

### `<gap/>`

`<gap/>` should *always* have an extent attribute specified. The value should always be some number. This number represents how many characters (approximately) are missing from the transcription due to illegibility. The value of `@extent` should be approximate, as we do not expect you to guess the *exact* number of characters that are illegible.

If there are two consecutive lines of illegible text, you should encode the extent for each line, each in a separate `<gap/>` element, separated by a `<lb/>`

#### Example
```
<gap extent="3"/>
<gap extent="27"/>
```

## `@facs`

`@facs` is short for "facsimile." This references a file name for an image that corresponds to the feature being encoded.

### `<surface>`

We only use `@facs` on the `<surface>` element, to say which page-level image file corresponds to the encoded page. If you do not know the names for the image files, you should leave this section blank, and the publication manager will add the specific names for the page image files.

## `@function`

The `@function` attribute specifies what a specific feature was used to communicate or convey. We only use this attribute on the `<metamark>` element.

### `<metamark>`

The `@function` attribute on `<metamark>` only takes one possible value: `insert`. You should use this attribute if the metamark is being used to indicate that a piece of text should be inserted.

#### Example
```
<metamark function="insert"/><add hand="#WSB1" place="supralinear">a</add>
```

## `@hand`

The `@hand` attribute should appear on any element describing a textual feature that involves handwriting. The only exceptions to this rule are when `<add>` or `<del>` elements occur inside `<subst>`, in which case `<add>` and `<del>` are assumed to have the same value on `@hand` as their parent. Additionally, `<del>` elements with a `@status` of "shortStart" or "shortEnd" do not require `@hand`.

This attribute allows you to specify whose handwriting is present in the text. For a list of known hands in the Burroughs documents, see the [hands.md](hands.md) file. This will give you a list of features (including type and color of ink, features of the script, etc.), which you should use to determine which hand to use.

### `<add>`

The `<add>` element should always take a `@hand` attribute, unless it is a child of `<subst>`. The value on `@hand` is a pointer to some `@xml:id`, which you can find on the [list of hands](hands.md).

#### Example
```
<add place="inline" hand="#typist">d</add>
```

### `<del>`

The `<del>` element should always take a `@hand` attribute, unless it is a child of `<subst>` or has a `@status` of "shortStart" or "shortEnd". The value on `@hand` is a pointer to some `@xml:id`, which you can find on the [list of hands](hands.md).

#### Example
```
<del rend="overwritten" hand="#proofreader1">d</add>
```

### `<subst>`

The `<subst>` element should always take a `@hand` attribute. The value on `@hand` is a pointer to some `@xml:id`, which you can find on the [list of hands](hands.md).

#### Example

```
<subst hand="#WSB2">
  <add place="supralinear">a</add>
  <del rend="crossedOut">s</del>
</subst>
```

## `@n`

The `@n` attribute is used to number features on texts.

### `<s>`

The usage of `@n` on `<s>` is slightly complicated. Most sentences will be numbered with a 3-digit number (corresponding to the numbering of sentences in the published version), followed by ".0.0". All sentence numbers should have 3 digits (if there are only one or two, you should precede the number with an appropriate number of zeros, i.e. "001" or "023").

*However*, some sentence numbers occur more than once in a given witness, so we use the first digit after the period to specify what occurrence that sentence is within the witness (e.g. the first occurrence gets "1", second gets "2", and so on).

The third number is used for if a sentence is split up over a page. For example, if a sentence starts in one page, and ends in another, the `<s>` element will be split in two. The first part will get "1", and the second part will get "2". If a sentence splits across a page, you will also need to use the [`@part` attribute](#part).

#### Examples
If the sentence only occurs once in the witness:
```
<s n="007.0.0">This sentence number only occurs once in the witness.</s>
```
If the sentence occurs more than once in the witness:
```
<s n="025.1.0">This sentence number occurs three times in the witness (first occurrence).</s>
<s n="025.2.0">This sentence number occurs three times in the witness (second occurrence).</s>
<s n="025.3.0">This sentence number occurs three times in the witness (third occurrence).</s>
```
If the sentence occurs once in the witness and is split along a page:
```
<surface facs="MSS2015-07-A" n="1">
  [...]
  <s n="348.0.1" part="I">This is the first part of</s>
</surface>
<surface facs="MSS2015-07-AA" n="2">
  <s n="348.0.2" part="F">a sentence that ends on the following page.</s>
</surface>
```
If the sentence occurs more than in the witness and is split along a page:
```
<surface facs="MSS2015-07-AAA" n="3">
  [...]
  <s n="015.1.1" part="I">This is the first occurrence of a sentence, and the sentence</s>
</surface>
<surface facs="MSS2015-07-AAAA" n="4">
  <s n="015.1.2" part="F">ends on the following page.</s>
</surface>
```

### `<surface>`

The `<surface>` element should have an `@n` attribute that just says what page number it is (independent of the Special Collections numbering system). So the first `<surface>` should be "1", the second "2", and so on.

## `@part`

The `@part` attribute is used to connect fragmented elements, by specifying which part of the feature is being encoded. The TEI provides the attributes "I", "M", and "F" for this purpose, but we will only use "I" and "F".

### `<s>`

The `@part` attribute should only be found on the `<s>` element, where the sentence is divided into more than one part. The first part should receive a value of "I" (for "initial"), and the second part should receive a value of "F" (for "final"). 

#### Example
```
<surface facs="MSS2015-07-A" n="1">
  [...]
  <s n="348.0.1" part="I">This is the first part of</s>
</surface>
<surface facs="MSS2015-07-AA" n="2">
  <s n="348.0.2" part="F">a sentence that ends on the following page.</s>
</surface>
```

## `@place`

The `@place` attribute specifies where on a page a given feature can be found. There is a separate closed list of values on `@place` for each element than can take it as an attribute. Make sure to read the element-specific guidelines for how to apply this attribute.

### `<add>`

The value of `@place` on `<add>` is determined by where the handwritten/typewritten addition appears in relation to the line being encoded or the larger page. The possible values are:

* `infralinear` - for when the addition occurs below the line being transcribed
* `supralinear` - for when the addition occurs above the line being transcribed 
* `inline` - for when the addition is placed in line with the normal text, but the addition *does not* overwrite other text
* `marginleft` - when the addition is in the left margin 
* `marginright` - when the addition is in the right margin 
* `margintop` - when the addition is in the top margin 
* `marginbottom` - when the addition is in the bottom margin 

### `<fw>`

The `@place` attribute on `<fw>` will specify where on the page the written page number is located. The possible values are:

* `top-left`
* `top-center`
* `top-right`
* `bottom-left`
* `bottom-center`
* `bottom-right`

## `@reason`

The `@reason` attribute is used to indicate *why* a given reading may be provided. Specifically, it is used in cases of obscured or illegible text, to indicate what caused the text to become unreadable. We only use `@reason` on `<unclear>`

### `<unclear>`

The `@reason` attribute is *required* on `<unclear>`. The possible values for `@reason` are:

* poorlyInked - This is used for typed letters and words that are unclear either because the ink was not properly applied to the page. This could happen because the typing mechanism was not properly depressed, or for some other reason. 
* illegible - This is used for instances where text (almost always handwritten) is illegible because the letters are irregularly formed (or in some cases not formed at all).
* obscured - This is used in cases where the text has been obscured by other writing, such as overwritten, overtyped, or crossed out text.
* damaged - This is used in instances where the physical documents themselves are damaged.
* flawedReproduction - In cases where you are working from a facsimile or digitized edition, you may end up using "flawedReproduction" (*although this is extremely rare*). This would be used in cases where you are confident that the illegibility is a result of an issue with the digitization or reproduction rather than the physical document itself. With documents transcribed from FSU's collections, you should try to check with the physical copy itself. Ideally, this value will never be used in cases where the encoder has access to the physical documents.

#### Example
```
d<unclear reason="poorlyInked">i</unclear>d
```

## `@rend`

The `@rend` attribute is used to describe renditional features (how the text or other (typo)graphical features appear on the page). Each element has its own allowable values for `@rend`, so make sure you read each subsection carefully.

### `<del>`

`<del>` requires a `@rend` attribute unless it has a `@status` of "shortStart" or "shortEnd".

* `erased` - for instances where the text has been erased
* `overwritten` - for when the *handwritten* deletion covers an existing line of text 
* `overtyped` - for when the *typed* deletion covers an existing line of text 
* `crossedOut` - for instances where the text has simply been crossed out

### `<hi>`

The `<hi>` element is used to encode any highlighting, underlining or cicling. As such, the values are:

* `circled`
* `underlined`
* `boxedblock` - (for instances of circles that look more like text being boxed in.)

### `<s>`

Very rarely, you will find a sentence that has a "false start" (i.e. Burroughs began typing and then stopped, flipped the page and began typing on the other side). This means that there are sentences at the bottom that are upside-down. In this case, `<s>` should take the value of "rotate180"

### `<surface>`

The `<surface>` element uses `@rend` to specify whether the surface is recto or verso (in cases where both sides have been written on). The possible values are:

* recto
* verso 

## `@status`

From the TEI guidelines, the `@status` attribute
 
> indicates the effect of the intervention, for example in the case of a deletion, strikeouts which include too much or too little text, or in the case of an addition, an insertion which duplicates some of the text already present.

### `<del>`

The `@status` attribute is only used on the `<del>` element. The possible values are:

* `excessEnd` - for instances when a physical deletion on the page continues past where the encoder assumes it ought to, based on context
* `excessStart` - for instances when a physical deletion on the page starts before the encoder assumes it ought to, based on context
* `shortEnd` - for instances where the deletion on the page does not follow through to the place where the encoder assumes the deletion should end based on context. Using "shortEnd" means that you should also refrain from using the `@hand` and `@rend` attributes.
* `shortStart` - for instances where the deletion on the page does not start at the place the encoder assumes the deletion should begin based on context. Using "shortEnd" means that you should also refrain from using the `@hand` and `@rend` attributes.

#### Examples
For an encoded section that looks like this:
> I really enjoyed ~attending the th~e concert yesterday

```
I really enjoyed 
<del rend="crossedOut" hand="#proofreader">attending the </del>
<del status="excessEnd">th</del>e concert yesterday.
```

For an encoded section that looks like this:
> I am an encoder for the ~Willia~m Burroughs Archive

```
I am an encoder for the <del rend="crossedOut" hand="#encoder">Willia</del><del status="implied">m </del>Burroughs Archive
```

## `@type`

The `@type` attribute is used to divide elements into different categories. In the Burroughs Archive, it is only used on `<fw>`, `<seg>`, and `<zone>`.

### `<fw>`

The `@type` attribute on `<fw>` should always be "pageNum".

### `<seg>`

The `@type` on `<seg>` will  always be "transposition".

### `<zone>`

The `<zone>` element will default to having no `@type` specified. However, if you need to mark the existence of a heading, you should use `<zone type="head">`. Or if the zone of text is a false start, you should use `<zone type="falseStart">`.

## `@xml:id`

The `@xml:id` is used to provide unique identifiers for the elements in the text. For our purposes, they will only be used on `<note>` and `<surface>`.

### `<note>`

A unique identifier should be given to every `<note>` element, by using the `@xml:id` attribute. The naming convention for `@xml:id` is "n" followed by 3 digits, indicating which number note you are on in the document (from start to finish). The first note should be "n001", the second "n002", the third "n003", and so on. 

### `<surface>`

The `@xml:id` on surface should be the page identifier provided by special collections. If you do not know these identifiers, talk to the publications manager.