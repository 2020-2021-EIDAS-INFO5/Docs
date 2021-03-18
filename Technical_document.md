---
output: 
  pdf_document:
    citation_package: natbib
    keep_tex: true
    fig_caption: true
    latex_engine: pdflatex
    template: ../svm-latex-ms.tex
bibliography: master.bib
header-includes:
  -  \usepackage{hyperref}
biblio-style: apsr
title: "The technical documentation of eIDAS project"
thanks: "Replication files are available on the author's Github account (http://github.com/svmiller). **Current version**: `r format(Sys.time(), '%B %d, %Y')`; **Corresponding author**: svmille@clemson.edu."
author:
- name: Houda EL AJI, Otba ZERAMDINI, Aleck Bilounga, Dima ASSI
  affiliation: Polytech Grenoble- Grenoble INP - Grenoble Alpes University
abstract: ""
date: "`r format(Sys.time(), '%B %d, %Y')`"
geometry: margin=1in
fontfamily: mathpazo
fontsize: 11pt
# spacing: double
endnote: no
---


# Introduction

This document is the technical documentation of our eIDAS project, an electronic signature web application that we called ` "PolySign" `. It is divided into four parts:
* Documentation on electronic signature regulations: [eIDAS](https://www.ssi.gouv.fr/entreprise/reglementation/confiance-numerique/le-reglement-eidas/) in Europe and [ANSSI](https://www.ssi.gouv.fr/) in France;
* The technical documentation of the user
* The technical documentation of the web application: The functioning and the current state of progress
* Known bugs within implementation. 



# Regulations


## The eIDAS regulation 

The `eIDAS` (Electronic IDentification And Trust Services) regulation applies to electronic identification, trust services and electronic documents. It aims to establish an interoperability framework for the different systems put in place within the Member States in order to promote the development of a digital trust market.
The regulation sets out requirements for the mutual recognition of electronic means of identification as well as of electronic signatures, for exchanges between public sector bodies and users. It excludes internal exchanges between administrations without direct impact on third parties as well as private signing documents.

The eIDAS regulation replaced Directive 1999/93 / EC. We find in eIDAS the concept of the three types of signature - low, substantial (SEA), high, which was already found in the said directive. However, the eIDAS regulation has brought new updates on this subject. It specifies that qualified electronic signatures and qualified electronic seals are produced respectively by means of:
* Qualified electronic signature creation devices;
* Qualified electronic seal creation devices.

Thus, what characterizes eIDAS the most is that in this case it is:
  * A uniform text of law valid for all of Europe which is uniform to the different national laws applied by each member state of the European Union. This speeds up the use of electronic signatures in cross-border transactions. 
  * An advanced electronic signature based on the prior obtaining of an electronic signature certificate. Qualified electronic signature certificates within the meaning of regulation n ° 910/2014 “eIDAS” are issued by qualified electronic certification service providers.
  * The ability to create qualified signatures in the cloud instead of using hardware.
  * A legal value for the simple electronic signature too. 



## The ANSSI regulation 

In France, the role of supervisory body for trust services is performed by `ANSSI` (The French National Agency for the Security of Information Systems). As such, it supports in particular:
-The definition of the technical modalities allowing compliance with the requirements of the regulation
- ANSSI is involved in the application of regulations in two ways: as a security guarantor for the "electronic identification" component and as a supervisory body for the "trust service" component.

ANSSI develops and maintains trust lists listing qualified trust service providers and the qualified trust services they provide;
In France, ANSSI plays the role of supervisory body for trust services
As such, it supports in particular:
the definition of the technical procedures allowing compliance with the requirements of the regulation;
the qualification of trusted service providers established on French territory which ensures the conformity certification of the devices for creating qualified electronic signatures or seals which is required by the eIDAS regulation.



Qualification process
 ANSSI takes a decision on the qualification of a trust service provider on the basis of a conformity assessment report prepared by a conformity assessment body meeting the criteria defined in the note [CRITERES_OEC]. This assessment report must make it possible to verify compliance with all the requirements applicable to the trust service provider as specified in this note, as well as the requirements applicable to the trust service that is the subject of the qualification request. . The qualification process is described in the document [QUALIF_SERV].

Duration of validity and maintenance of qualification
The qualification of the trust service provider is issued for a maximum period of two years, in accordance with Article 20 of the [eIDAS] Regulation. To allow uninterrupted maintenance of the qualified status of a trusted service, a conformity assessment report drawn up by an organization meeting the criteria of [CRITERES_OEC] must be sent to ANSSI at least three months before the expiration of the qualification.
Conformity assessment criteria
The assessment must make it possible to demonstrate compliance with the requirements of the [eIDAS] regulation applicable to all qualified trust service providers, specified in the following articles: 5 (1) Protection and processing of personal data; 13 (2) Limitation of liability; 15 Accessibility; 19 (1) Risk management; 19 (2) Notification of incidents; 24 (2) .a Information of the supervisory body relating to changes in services; o b Expertise, reliability, experience and qualification of staff and subcontractors; o c Maintaining sufficient financial resources and / or liability insurance; o Information of the conditions and limits of use of the services; o e Use of reliable products and systems, safety and reliability of processes; o f Use of reliable systems for data storage; o g Measures against falsification and theft of data; o j Lawful processing of personal data. Compliance with standard [EN_ 319_401] and the additions specified in chapter II.3 of this document allows a presumption of conformity to these requirements to be made.



![Alt text](./media/ANSSI_recommandation.png "Title")



We decided to use the RSA asymmetric encryption algorithm. So we decided to choose an encryption with a pair of keys (one private and one public). According to the ANSSI technical specification for RSA encryption, the size of the public keys must be 3072 bytes. So we decided to generate a key pair for each user of size 3072 bytes:


![Alt text](./media/KeyPair.png "Title")


En ce qui conserne les algorithmes de hachages, l'ANSSI préconise d'utiliser l'algorithme de hashage SHA-256. 


# The technical documentation of the user
In this part, we detail how a user can use our web application :

Fistly,An administrator can create a user account by accessing the userEntity form and click on the button indicate below

![Alt text](./media/Usercreate.jpg "Title")

The creation form consists of two tabs, the administrator fills in all informations of the new user

![Alt text](./media/usercreate2.jpg "Title")

And then he clicks on the next button to assign him a role in the organization
![Alt text](./media/usercreate3.png "Title")

Once the "finish" button is clicked the user receives an email with a password and a username to connect

![Alt text](./media/usercreate4.jpg "Title")

![Alt text](./media/mail_confirmation.png "Title")
Now the user can log in by accessing the application

![Alt text](./media/connection.jpg "Title")
For the first connection the user must verify his email address

![Alt text](./media/verification.png "Title")

![Alt text](./media/verification_mail.jpg "Title")

![Alt text](./media/mobile_verification.jpg "Title")

![Alt text](./media/mobileoftp.jpg "Title")

![Alt text](./media/insertOTPcode.jpg "Title")

![Alt text](./media/New_Password.jpg "Title")

![Alt text](./media/createSignprocess.jpg "Title")

![Alt text](./media/createSignprocess2.jpg "Title")

![Alt text](./media/createSignprocess3.jpg "Title")

![Alt text](./media/createSignprocess4.jpg "Title")

![Alt text](./media/createSignprocess5.jpg "Title")

![Alt text](./media/placeholder1.jpg "Title")

![Alt text](./media/placeholder2.png "Title")





































```markdown

# Introduction

**Lorem ipsum** dolor *sit amet*. 

- Single asterisks italicize text *like this*. 
- Double asterisks embolden text **like this**.

Start a new paragraph with a blank line separating paragraphs.

- This will start an unordered list environment, and this will be the first item.
- This will be a second item.
- A third item.
    - Four spaces and a dash create a sublist and this item in it.
- The fourth item.
    
1. This starts a numerical list.
2. This is no. 2 in the numerical list.
    
# This Starts A New Section
## This is a Subsection
### This is a Subsubsection
#### This starts a Paragraph Block.

> This will create a block quote, if you want one.
Want a table? This will create one.

Table Header  | Second Header
------------- | -------------
Table Cell    | Cell 2
Cell 3        | Cell 4 

Note that the separators *do not* have to be aligned.

Want an image? This will do it.

![caption for my image](path/to/image.jpg)

`fig_caption: yes` will provide a caption. Put that in the YAML metadata.

Almost forgot about creating a footnote.[^1] This will do it again.[^2]

[^1]: The first footnote
[^2]: The second footnote

Want to cite something? 

- Find your biblatexkey in your bib file.
- Put an @ before it, like @smith1984, or whatever it is.
- @smith1984 creates an in-text citation (e.g. Smith (1984) says...)
- [@smith1984] creates a parenthetical citation (Smith, 1984)

That'll also automatically create a reference list at the end of the document.

[In-text link to Google](http://google.com) as well.
```


# Using R Markdown with Knitr



```{r, eval=FALSE, tidy = TRUE}
library(stevemisc)
data(uniondensity)
M1 <- lm(union ~ left + size + concen, data=uniondensity)
library(arm)
coefplot(M1)
```

```{r, eval=TRUE, tidy = TRUE, cache=FALSE, fig.cap="A Coefficient Plot", message=F, warning=F}
library(stevemisc)
data(uniondensity)
M1 <- lm(union ~ left + size + concen, data=uniondensity)
library(arm)
coefplot(M1)
```




<!--
# References
\setlength{\parindent}{-0.2in}
\setlength{\leftskip}{0.2in}
\setlength{\parskip}{8pt}
\vspace*{-0.2in}
\noindent
-->
