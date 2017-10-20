# The TEI Header

*The TEI header* (`<teiHeader>`) *is used to record metadata about the witness being encoded. It should occur at the start of every document, before the* `<sourceDoc>`. *This document is primarily for the use of the publications manager or library staff. Student encoders do not need to fill out the* `<teiHeader>`, *with the exception of the* `<revisionDesc>`.

## For encoders - `<revisionDesc>`

Whenever you finish a major portion of the encoding process, you should include a `<change>` element in the `<revisionDesc>`.

Major changes include:

* finishing encoding the document (or finishing a pass of a document, if you are doing it in multiple steps)
* finishing the corrections entry after the XML proofing
* finishing the corrections entry after the *display* proofing
* conducting a major systemic change across all documents (publication manager should be the only one doing this)

A change element should look like this:

```
<change who="#yourid" when="YYYY-MM-DD">A brief description of your change</change>
```

Ask the publication manager for your ID. Make sure that you put your changes in reverse chronological order (i.e. the most recent change should go to the top).

## Template for the TEI Header 

Since much of the TEI Header is repeatable, we are going to simply put a template in this file, with comments indicating the function of the element. If the element content or attribute values are the same across all documents, we will indicate it. If not, we will include possible values or the best practices for filling the section out.

**Please note that this whole section should be checked with the metadata librarian before publication.**

```
<teiHeader>
      <fileDesc>
         <titleStmt>
            <title><!-- Title of the document, as it was published --></title>
            <author>William S. Burroughs</author> <!-- this should remain the same, unless we expand our publication policies beyond the works of Burroughs -->
            <sponsor>Florida State University Libraries</sponsor>
            <sponsor>Florida State University Department of English</sponsor>
         </titleStmt>
         <publicationStmt>
            <authority>FSU</authority>
            <distributor>FSU</distributor> 
            <idno type="IID"><!-- this should contain the IID as it is determined by the FSU Libraries staff. Contact someone in the Digital Library or Office of Digital Research and Scholarship, if you do not know what this is. --></idno> 
            <publisher>The Burroughs Archive</publisher>
         </publicationStmt>
         <sourceDesc>
            <biblFull>
               <titleStmt>
                  <title><!-- Title of the document, as it was published --></title> 
                  <title type="sub"><!-- optional; only use if the document has a subtitle --></title>
                 <author>
                   <persName type="personal" ref="http://id.loc.gov/authorities/names/n79026862" source="http://id.loc.gov/authorities/names" key="lcnaf">
                     <forename>William</forename> 
                     <addName>S.</addName> 
                     <surname>Burroughs</surname>
                   </persName> 
                   <date>1914-1997</date>
                 </author> <!-- this should remain the same, unless we expand our publication policies beyond the works of Burroughs -->
               </titleStmt>
               <editionStmt>
                  <edition><!-- This is the name of the witness. Usually this is the name of the Institution that holds the physical copy + whether it is a manuscript or a typescript. It could also involve a statement about the revision status or some other way of disambiguating it from the other witnesses. --></edition> 
               </editionStmt>
               <extent><!-- Number of *physical pages* (not the number of surfaces; the number of actual sheets) --></extent>
               <publicationStmt>
                 <distributor>Florida State University</distributor>
                  <address>
                     <addrLine>Special Collections &amp; Archives, Florida State University Libraries, Tallahassee, Florida.</addrLine> <!-- This will *usually* remain the same, unless we receive a witness from another institution -->
                  </address>
                  <availability>
                     <licence>Use of this item is provided for non-commercial, personal, educational, and research use only. Florida State University Libraries is providing access to these materials for educational and research purposes and makes no warranty with regard to their use for other purposes. The written permission of the copyright owners and/or other rights holders (such as holders of publicity and/or privacy rights) is required for distribution, reproduction, or other use of protected items beyond that allowed by fair use or other statutory exemptions (see Title 17, U.S.C.). For information about the copyright and reproduction rights for this item, please contact Special Collections &amp; Archives, Florida State University Libraries, Tallahassee, Florida: https://www.lib.fsu.edu/department/special-collections-archives.</licence> <!-- This will remain the same unless the estate changes the restrictions on this item. -->
                  </availability>
                  <date from="1970" to="1979"><!-- change according to the estimated or known dates of composition --></date>
               </publicationStmt>
            </biblFull>
         </sourceDesc>
      </fileDesc>
      <profileDesc>
         <textClass>
           <keywords scheme="http://id.loc.gov/authorities/genreForms" corresp="lcgft" ana="http://id.loc.gov/authorities/genreForms/gf2014026339"> 
               <list>
                  <item>Fiction</item> <!-- Any genre term can be used here, but check with the LOC genre authorities list. Also, make sure to run this by the metadata librarian -->
               </list>
            </keywords>
         </textClass>
      </profileDesc>
     <revisionDesc>
       <!-- This is the one part of the TEI Header that encoders should edit. After any major changes, they should enter a description of the change, along with the date and their name key -->
       <change when="2017-10-20" who="#scstanley">Updated the TEI header documentation.</change>
     </revisionDesc>
   </teiHeader>
```