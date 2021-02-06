
# Purpose
An example template of files for variants of a solution architecture in a documentation-as-code approach.

# Assumption(s)
- The text-based structure/format is in AsciiDoc ( https://github.com/asciidoc/asciidoc ) format (see/edit \*.adoc files) and can review a simple tutorial ( https://github.com/bwgartner/suse-doc/tree/master/AsciiDoc)
  - the default structure is generic ... classic book - chapter - section - sub-section
    - other variations are also available, see
      Enterprise Architecture - [ReadMe-EA.md](./ReadMe-EA.md)
      Reference Architecture - [ReadMe-RA.md](./ReadMe-RA.md)
  - much of the sample text placeholder content is from the ( https://loremipsum.io/ ) generator ... so this is where you substitute your content.
    - Focus on anything that cites "FixMe"
- To create any number of multiple output formats, install and leverage DAPS ( https://github.com/openSUSE/daps )
  - html, single-html, pdf, epub

# Validation
- Obtain this document's template content
  - git clone "ThisGitHubRepoURL" (to make a local copy)
  - download either master (zip) or the latest release (zip/tar.gz), then unpack it
  - cd to your local directory where it landed and was uncompressed
- Test that you have all the tooling in place to generate an output
  - e.g. daps --force -d DC-SA html
  - test with a web browser, open the file:///localDirectoryName/build/SA/html/SA_draft/index.html

# Usage / Process
- At this point, you can now start editing the configuration/structure/content to meet your needs
  - NOTE: every portion of text that cites "FixMe" is a flag to encourage modification
  - in the top-level directory
    - for the default configuration/structure (chapter/section/sub-section)
      - review/edit the DAPS configuration file [DC-SA](./DC-SA)
        - comment out any ADOC_ATTRIBUTES line to skip that respective section
        - uncomment any ADOC_ATTRIBUTES lines and set the value to 1 to include the respective content
  - in the main "adoc" directory
    - review/edit the [adoc/SA.adoc](./adoc/SA.adoc) main file that pulls in the selected sections
      - if the respective ADOC_ATTRIBUTES value is set (value = 1 and uncommented) in the [DC-SA](./DC-SA) file, then the conditional "ifdef" will include that content in the output
      - if you need fewer chapters, feel free to comment out the extra "include" of chapters 2 (ii) - 7 (vii)
    - review/edit the [adoc/SA_vars.adoc](./adoc/SA_vars.adoc) file to change global variable settings, like
      - useCase
      - companyName
      - title (relative to your attribute setting)
      - author information
      - github references
    - review/edit the general sections, that are generally included
      - [adoc/SA-Preface.adoc](./adoc/SA-Preface.adoc)
      - [adoc/SA-Summary.adoc](./adoc/SA-Summary.adoc)
    - review/edit the general sections, that your ADOC_ATTRIBUTES settings will include
      - [adoc/SA-References.adoc](./adoc/SA-References.adoc)
      - [adoc/SA-Appendix.adoc](./adoc/SA-Appendix.adoc)
  in the various chapter directories aka Roman numeral sequences
    - review/edit the chapter/section/sub-section content, that you wish to include
      - [adoc/i/SA.adoc](./adoc/i/SA.adoc) aka Introduction
      - [adoc/ii/SA.adoc](./adoc/ii/SA.adoc)
      - etc
  - as you edit the modular text content snippets, create an output format
    - daps --force -d DC-SA format
      - where format might be "pdf", "html", "html --single", "epub" and others are also available
      - then review the output and continually iterate until you have your content complete
  - miscellaneous 
    - you can also add images/media content as needed in those subdirectories
    - do not forget to check in your iterations as well to have a source repository and ability to rollback to a known working state

# Feedback
- feel free to provide feedback, ask questions or even submit pull request
