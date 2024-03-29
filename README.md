## Parent Project 

 * List of Git repositories in this project: [https://github.com/sucho-oai](https://github.com/sucho-oai)
 * Description and details for this project: [https://github.com/sucho-oai/admin](https://github.com/sucho-oai/admin)

## About this repository

This is a repository of the full harvest of the OAI-PMH server: http://journal.ceramology.gov.ua/index.php/index/oai using [metha](https://github.com/miku/metha)

## About this project

The purpose of this project to take harvests of as many Ukrainian OAI-PMH repository servers (metadata and source files) as possible. Refer [https://github.com/sucho-oai](https://github.com/sucho-oai) for all the repositories harvested. 1 Git repository per OAI-PMH repository endpoint.

Currently over 800 Ukrainian OAI endpoints have been documented, and harvests started

### What is a OAI-PMH repository?

OAI-PMH is an interoperability protocol used by archival and document repository servers. 

### What is a document repository??

Libraries, universities, institutions, reasearch organisations, academic publishers and more store, manage and publish their important documents - suchs as jounrals, thesis, research, iamges etc.. in doucment repository server - such as ePrints, OJS or Dspace.

Repositories harvested include (but not limited to) academic journals, thesis PDFs, conference papers, images/photos, maps, scanned paintings and historical phtos - predominently from libraries (Univerities, regional, government, national and research), galleries, museums, government departments etc...

### Why? 

With the intent that if a Ukrainian repository is taken offline - it can be rebuild using these source files.

Repository servers from the various Ukrainian organisation contain a huge collection of the knowledge, history and digital artifacts of Ukraines cultural heritage.

Should anything happen to the physical entity - such as a library or gallery being destroyed, digital copies of their content is avialable in their document repositories. Should these digital copies become inaccessible (either servers physically destroyed or offline) this project (as well as [SUCHO.org](https://sucho.org) and the [Internet Archive](https://archive.org)) aim to have copies of the source OAI data and files.

## SUCHO

This project and repositories align with the [SUCHO.org](https://sucho.org) Saving Ukrainian Cultural Heritage Online project. SUCHO is doing an AMAZING job archiving to the [Internet Archive](https://archive.org) Ukraines curltural hertiage (libraries, galleries, musuems etc..) web site as possible as quickly as possible. It's focus is to crawl and archive Ukraines web pages in WACZ format - so they will be availble in perpetuity. If you are a cultural heritage profesional please consider volunteering.

## Where are we at?

This project has 4 parts:

 * 1: Archive as many Ukrainian OAI-PMH servers as possible and make the source OAI data avilable publically in Git
 * 2: Provide a single xml file per metadataPrefix/format per repository via our CDN for easy viewing/downloading of a full repository
 * 3: Use SUCHOs OAI file downloader scripts to harvest as many of the item files (PDFs etc..) that are linked in the OAI data
  * 3a: Publish the item files publically to an S3/B2 bucket and via the CDN
  * 3b: Publish the item files directly to the Internet ARchive or SUCHO - whichever is appropriate
 * 4: Transform and publish this data and files back to SUCHO in a format best suited to their processes

Parts 1 and 2 are currently in progress

### Why OAI-PMH

OAI-PMH is a standard which most academic and archival software repositores use for interoperability.

This projects focus is on OAI-PMH, as in the OAI data is the full metadata for the repository items and links to the item file - be that MARC, Dublin Core, MARC XML or other.

This metadata can be imported back into a new repository if and when requuired.

### Why Metha

Metha is a fantasic suite of oai tools that include harvesting (incrementaly and full), viewing, querying, and inspecting OAI data. 
Metha saves the OAI-PMH data in gzipped xml files in batches of records - which makes it easy to store in Git. 

For convienciance I have used `metha-cat` to create 1 big xml file per metadataPreifx/format per oai host and uploaded these to BackBlaze B2 (simialr to AWS S3) and available via the CloudFlare CDN - links below. These files can be too large for Git repositories.

## Details

OAI Server: 

 * http://journal.ceramology.gov.ua/index.php/index/oai

BackBlaze B2 public bucket:

 * Name: sucho-oai
 * URL:
https://f001.backblazeb2.com/file/sucho-oai/
 * S3 URL: https://sucho-oai.s3.us-west-001.backblazeb2.com/

Cloudflare CDN:

 * https://cdn.biblio.ai/file/sucho-oai/

Formats/metadataPrefixes harvested: oai_dc, oai_marc, marcxml, marc, mods,mets

## Complete OAI-PMH feed per format

* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/oai_dc.xml
* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/oai_marc.xml
* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/marcxml.xml
* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/marc.xml
* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/mods.xml
* https://cdn.biblio.ai/file/sucho-oai/sucho-journal.ceramology.gov.ua__index.php__index__oai/mets.xml


**Note: If the above xmls files are blank, it means that the harvested repository was not publishing in this metadata format. If this repository is blank except for the README,- it means that the OAI-PMH server has not been fully harvested yet or isn unable to be harvested**

## Example OAI file

Below is an example of the data stored in the OAI file - this one shows DC (Dublin Core) with the link to the soruce item file highlighted. These item files beed to be downloaded and stored as a seperate process

![DC OAI sample](https://raw.githubusercontent.com/sucho-oai/admin/master/dc-example.png)
