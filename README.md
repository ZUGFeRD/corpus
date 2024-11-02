# corpus
Collection of real, sample and test elecronic invoices, usually ZUGFeRD, partly with artificial errors

# Samples for Statutory German Domestic B2B E-Invoices

As german businesses have to be able to accept/read/understand domestic B2B e-invoices as of January 1st, 2025
([the law](https://www.recht.bund.de/bgbl/1/2024/108/VO), in particular art. 23 on p. 23) and a bit of it's  
[background]( https://medium.com/@jochen.staerk/why-and-how-germany-bans-b2b-paper-invoices-a4c7977f314a))
and samples are nowhere in sight the [XML-Rechnung](https://github.com/ZUGFeRD/corpus/tree/master/XML-Rechnung)-Folder is an attempt to 
demonstrate how temporary, makeshift, inofficial samples 
can be created based on a part of AWV's [ZUGFeRD Infopaket](https://www.ferd-net.de/ZUGFeRD-Download) using [Mustang](https://www.mustangproject.org/?mtm_campaign=b2bsamples) until someone feels responsible to release official samples.
Please note that the CEN has [UBL](https://github.com/ConnectingEurope/eInvoicing-EN16931/tree/master/ubl/examples) and [CII](https://github.com/ConnectingEurope/eInvoicing-EN16931/tree/master/cii/examples) examples.


## Background

We need to parse invoices calculated according to the rules laid down in [EN16931-2](https://www.beuth.de/de/technische-regel/din-cen-ts-16931-2/274991011) using the [known codelists](https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Registry+of+supporting+artefacts+to+implement+EN16931) as attributes.
According to [EN16931-1](https://www.beuth.de/en/standard/din-en-16931-1/314992770), we have to support the XML syntaxes CII and UBL.
Additionally, according to a [letter](https://www.dstv.de/wp-content/uploads/2023/10/BMF_2023-0922192-R.pdf) of the BMF, we have to assume that we also have to be able to parse CII embedded into PDF/A files, i.e. Factur-X~ZUGFeRD.
I.e., we create three directories, FX for Factur-X, CII and UBL.
As a company you can decide which format to send but you will have to accept all three,

## 1. PDF
Get the ZUGFeRD 2.2 samples by downloading the
[Infopaket](https://www.ferd-net.de/standards/zugferd-2.2/index.html?changelang=4)

We put the samples (Factur-X=PDF files) from the EN16931 and XRechnung reference profile 
(they are EN16931 as well) in the FX folder. 

## 2. CII
Get  [Mustang](https://www.mustangproject.org/commandline/?mtm_campaign=b2bsamples)


We can either use Mustang `--action extract` or we open 
the files in a PDF reader and save their embedded factur-x.xml's 
(or, in case of the xrechnung reference profile, the xrechnung.xml)
as <pdffilename>.cii.xml.

## 3. UBL

We switch to the UBL directory and use
`--action ubl` to convert all CII files to UBL. 
(Mustang uses Philip Helger's great open source 
[CII2UBL](https://github.com/phax/en16931-cii2ubl) 
for that purpose there).

Please note that  `--action validate` will work on FX and CII
but not yet on UBL files ([issue](https://github.com/ZUGFeRD/mustangproject/issues/337)), the offline viewer 
[Quba](https://quba-viewer.org/?mtm_campaign=b2bsamples) should still be capable to render all three formats.


## 4. Do something with it

And don't forget to have fun.

Kind regards,\
Your Mustang Team\
Jochen Stärk\
Chief [Mustangproject.org](https://mustangproject.org/?mtm_campaign=b2bsamples) ZUGFeRD Amatuer\
jstaerk[at]usegroup.de

## Purpose
These are basically test files for two categories of software: ZUGFeRD **readers** should understand the correct files and ZUGFeRD **validators** should (not report errors in the correct files and) additionally flag the errors in the incorrect files.

## Additional links

* [PDF/A attachment with flat array structure](https://web.archive.org/web/20170519002523/http://www.pdflib.com/fileadmin/pdflib/pcos-cookbook/pdf/zugferd_invoice.pdf)
