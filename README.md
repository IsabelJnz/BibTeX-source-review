# BibTeX-source-review

<a href="https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#1-introduction"> 1. Introduction </a>
<a href="https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#2-description-of-the-rules"> 2. Description of the Rules </a>
<a href="[https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#1-introduction](https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#3-usage-guide)"> 3. Usage Guide </a>
<a href="[https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#1-introduction](https://github.com/IsabelJnz/BibTeX-source-review/blob/main/README.md#4-how-to-adapt-an-excisting-or-add-a-new-rule-for-the-bibtexcontrol-program)"> 4. How to adapt an excisting or add a new rule for the BibtexControl program </a>


## 1. Introduction

This repository contains a source checker for BibTex files in LaTeX. It is possible to check the sources of the any thesis for their correctness. Thereby it is possible to adapt or add style rules to enable an individual check. The current version complies with the current standards.

<hr noshade color=#FF0000>

## 2. Description of the Rules

Those follwoing rules can be adapted to the styling rules of your thesis.

<hr noshade color=#FF0000>

### Style Rules

- Checks if Bibtex format is correct and gives suggestions what it could be
- Remove umlauts and special characters
- WARNING: remove months and days so that only the year is given
- WARNING: Abbreviations in the journal should be removed
- WARNING: DOI must be specified
- WARNING: The place of publication must be specified
- WARNING: Corr and Arxiv must be removed
- WARNING: Page numbers must be present everywhere
- WARNING: No more than three authors may be given, abbreviate with 'and others' afterwards
- WARNING: language recognition → German or English source???
- WARNING: Adjust edition spelling
- WARNING: Correct formulas
- WARNING: Remove URL
- WARNING: Correct spelling of the edition

<hr noshade color=#FF0000>

## 3. Usage Guide

#### Start using the preprocessing file to check the sources types. You will receive type suggestions in case there are discrepancies in the characteristics of the BibTeX formats.

1. Export the data of the bib file into a simple txt file.

2. Please replace the 'path_source' with the location of your txt file:

>path_source='bibtex.txt'

>...


3. Please replace the 'path_final' with the location of your requested txt file:

>...

>path_final='preCheck.txt'


4. You receive another txt file ('preCheck'). Now you have the chance to adapte your sources. Therefore you can take a look at the WARNING recommendations. After adating the txt file please safe it.

<hr noshade color=#FF0000>

#### Continue with the BibtexControl file and use the 'preCheck' file from the preprocessing process

1. Please replace the 'path_preCheck' with the location of your txt file:

>...

>path_preCheck='preCheck.txt'

>...

2. Please replace the 'path_updatedBibtex' with the location of your requested txt file:

>...

>path_updatedBibtex='updatedBibtex.txt'

3. Take a look at the WARNING recommendations and adapt the txt file and delete the WARNING paragraph.



<strong>FYI: For another BibTex check please remove the old WARNING for a better overview!</strong>

<hr noshade color=#FF0000>

## 4. How to adapt an excisting or add a new rule for the BibtexControl program

<body>
    
<p>function for setting the rules:

    def get_date(sources):
        sources_final=[]

        for x in range(0,len(sources)-1):
            tmp=sources[x]

            strtmp="".join(tmp)
            strtmp=strtmp.lower()

            # with the function find() you can check every BibTeX item. You can search for a specific substring.
            # for checking a specific BibTex format use '@' and the name of the format
            y=strtmp.find('@...')
            
            sources_final.append(tmp) 

            # -1 means that no substring with the condition above was found
            # add specific substring condition to check the BibTeX items individually
            if y!=-1:
            sk1=strtmp.find('{', y)
            
            
            # add a condition that triggers a WARNING
            if sum > 5:
                del sources_final[-1]
                sources_final.append(f'\n{tmp} |----> WARNING: Please add your warning text ---- \n')
            
    return sources_final
</p>
</body>

<hr noshade color=#FF0000>
