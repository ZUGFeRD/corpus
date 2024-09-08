# Samples for Statutory German Domestic B2B E-Invoices

As german businesses have to be able to accept/read/understand domestic B2B e-invoices as of January 1st, 2025
([the law](https://www.recht.bund.de/bgbl/1/2024/108/VO), in particular art. 23 on p. 23) and a bit of it's  
[background]( https://medium.com/@jochen.staerk/why-and-how-germany-bans-b2b-paper-invoices-a4c7977f314a))
and samples are nowhere in sight this is an attempt to 
demonstrate how temporary, makeshift, inofficial samples 
can be created based on a part of AWV's [ZUGFeRD Infopaket](https://www.ferd-net.de/ZUGFeRD-Download) using [Mustang](https://www.mustangproject.org/?mtm_campaign=b2bsamples) until someone feels responsible to release official samples. 

## Background

We need to parse invoices calculated according to the rules laid down in [EN16931-2](https://www.beuth.de/de/technische-regel/din-cen-ts-16931-2/274991011) using the [known codelists](https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Registry+of+supporting+artefacts+to+implement+EN16931) as attributes.
According to [EN16931-1](https://www.beuth.de/en/standard/din-en-16931-1/314992770), we have to support the XML syntaxes CII and UBL.
Additionally, according to a [letter](https://www.dstv.de/wp-content/uploads/2023/10/BMF_2023-0922192-R.pdf) of the BMF, we have to assume that we also have to be able to parse CII embedded into PDF/A files, i.e. Factur-X~ZUGFeRD.
I.e., we create three directories, FX for Factur-X, CII and UBL.

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

## EeISI_300_CENfullmodel
The file 
not_validating_full_invoice_based_onTest_EeISI_300_CENfullmodel
is taken from the Eigor-Part of 
https://github.com/AgID/EeISI-mapper/ 
and converted to CII and UBL. This was the original source, 
from which you can see that "def" is e.g. BT-14:
```
<?xml version="1.0" encoding="UTF-8"?>
<SEMANTIC-INVOICE>
    <BT-1>Test_EeISI_100</BT-1>
    <BT-2>2018-11-12</BT-2>
    <BT-3>380</BT-3>
    <BT-5>EUR</BT-5>
    <BT-6>NOK</BT-6>
    <BT-8>35</BT-8>
    <BT-9>2018-11-30</BT-9>
    <BT-10>123</BT-10>
    <BT-11>456</BT-11>
    <BT-12>789</BT-12>
    <BT-13>abc</BT-13>
    <BT-14>def</BT-14>
    <BT-15>ghi</BT-15>
    <BT-16>lmn</BT-16>
    <BT-17>opq</BT-17>
    <BT-18 scheme="0090">rst</BT-18>
    <BT-19>uvz</BT-19>
    <BT-20>total amount</BT-20>
    <BG-1>
        <BT-21>#AAA#</BT-21>
        <BT-22>invoice note text</BT-22>
    </BG-1>
    <BG-1>
        <BT-21>#AAA#</BT-21>
        <BT-22>invoice note text 2</BT-22>
    </BG-1>
    <BG-2>
        <BT-23>BT-23 Business Process Type</BT-23>
        <BT-24>urn:cen.eu:en16931:2017</BT-24>
    </BG-2>
    <BG-3>
        <BT-25>abc123</BT-25>
        <BT-26>2018-10-04</BT-26>
    </BG-3>
    <BG-3>
        <BT-25>abc456</BT-25>
        <BT-26>2018-10-01</BT-26>
    </BG-3>
    <BG-4>
        <BT-27>Seller name</BT-27>
        <BT-28>Seller trading name</BT-28>
        <BT-29 scheme="0100">Seller identifier 1</BT-29>
        <BT-29 scheme="0110">Seller identifier 2</BT-29>
        <BT-30 scheme="0310">Seller legal identifier</BT-30>
        <BT-31>DE12345677</BT-31>
        <BT-32>DE49294093</BT-32>
        <BT-33>Seller additional legal information</BT-33>
        <BT-34 scheme="SMTP">Seller electronic address</BT-34>
        <BG-5>
            <BT-35>Seller address line 1</BT-35>
            <BT-36>Seller address line 2</BT-36>
            <BT-162>Seller address line 3</BT-162>
            <BT-37>Seller city</BT-37>
            <BT-38>12345</BT-38>
            <BT-39>Seller country subdivision</BT-39>
            <BT-40>DE</BT-40>
        </BG-5>
        <BG-6>
            <BT-41>Seller contact point</BT-41>
            <BT-42>+41 345 654455</BT-42>
            <BT-43>seller@contact.de</BT-43>
        </BG-6>
    </BG-4>
    <BG-7>
        <BT-44>Buyer name</BT-44>
        <BT-45>Buyer trading name</BT-45>
        <BT-46 scheme="0190">Buyer identifier</BT-46>
        <BT-47 scheme="0089">Buyer legal registration identifier</BT-47>
        <BT-48>IE394838894</BT-48>
        <BT-49 scheme="DE:SMTP">Buyer electronic address</BT-49>
        <BG-8>
            <BT-50>Buyer address line 1</BT-50>
            <BT-51>Buyer address line 2</BT-51>
            <BT-163>Buyer address line 3</BT-163>
            <BT-52>Buyer city</BT-52>
            <BT-53>34562</BT-53>
            <BT-54>Buyer country subdivision</BT-54>
            <BT-55>IE</BT-55>
        </BG-8>
        <BG-9>
            <BT-56>Buyer contact point</BT-56>
            <BT-57>+353 2948584</BT-57>
            <BT-58>buyer@contact.ie</BT-58>
        </BG-9>
    </BG-7>
    <BG-10>
        <BT-59>Payee name</BT-59>
        <BT-60 scheme="0098">Payee identifier</BT-60>
        <BT-61 scheme="0099">Payee legal registration identifier</BT-61>
    </BG-10>
    <BG-11>
        <BT-62>Tax representative name</BT-62>
        <BT-63>DE3949053</BT-63>
        <BG-12>
            <BT-64>Tax representative address line 1</BT-64>
            <BT-65>Tax representative address line 2</BT-65>
            <BT-164>Tax representative address line 3</BT-164>
            <BT-66>Tax representative city</BT-66>
            <BT-67>23455</BT-67>
            <BT-68>Tax representative country subdivision</BT-68>
            <BT-69>DE</BT-69>
        </BG-12>
    </BG-11>
    <BG-13>
        <BT-70>Deliver to party name</BT-70>
        <BT-71 scheme="0045">deliver location identifier</BT-71>
        <BT-72>2018-12-04</BT-72>
        <BG-14>
            <BT-73>2018-11-12</BT-73>
            <BT-74>2018-11-30</BT-74>
        </BG-14>
        <BG-15>
            <BT-75>Deliver to address line 1</BT-75>
            <BT-76>Deliver to address line 2</BT-76>
            <BT-165>Deliver to address line 3</BT-165>
            <BT-77>Deliver to city</BT-77>
            <BT-78>98765</BT-78>
            <BT-79>Deliver to country subdivision</BT-79>
            <BT-80>IE</BT-80>
        </BG-15>
    </BG-13>
    <BG-16>
        <BT-81>4</BT-81>
        <BT-82>SEPA</BT-82>
        <BT-83>Remittance information</BT-83>
        <BG-17>
            <BT-84>IT1212341234123412</BT-84>
            <BT-85>Payment account name</BT-85>
            <BT-86>BSCTCH22</BT-86>
        </BG-17>
        <BG-17>
            <BT-84>IT1212341234123413</BT-84>
            <BT-85>Payment account name 2</BT-85>
            <BT-86>BSCTCH22</BT-86>
        </BG-17>
        <BG-18>
            <BT-87>1234</BT-87>
            <BT-88>Payment card holder name</BT-88>
        </BG-18>
        <BG-19>
            <BT-89>Mandate reference identifier</BT-89>
            <BT-90>Bank assigned creditor identifier</BT-90>
            <BT-91>Debited account identifier</BT-91>
        </BG-19>
    </BG-16>
    <BG-20>
        <BT-92>10.00</BT-92>
        <BT-93>1000.00</BT-93>
        <BT-94>1.00</BT-94>
        <BT-95>S</BT-95>
        <BT-96>5.00</BT-96>
        <BT-97>Doc allowance reason text</BT-97>
        <BT-98>55</BT-98>
    </BG-20>
    <BG-21>
        <BT-99>10.00</BT-99>
        <BT-100>1000.00</BT-100>
        <BT-101>1.00</BT-101>
        <BT-102>S</BT-102>
        <BT-103>5.00</BT-103>
        <BT-104>Doc charge reason text</BT-104>
        <BT-105>AAA</BT-105>
    </BG-21>
    <BG-22>
        <BT-106>2000.00</BT-106>
        <BT-107>10.00</BT-107>
        <BT-108>10.00</BT-108>
        <BT-109>2000.00</BT-109>
        <BT-110>50</BT-110>
        <BT-111>46</BT-111>
        <BT-112>2050</BT-112>
        <BT-113>0</BT-113>
        <BT-114>0</BT-114>
        <BT-115>2050</BT-115>
    </BG-22>
    <BG-23>
        <BT-116>1000</BT-116>
        <BT-117>50</BT-117>
        <BT-118>S</BT-118>
        <BT-119>5.00</BT-119>
    </BG-23>
    <BG-23>
        <BT-116>1000</BT-116>
        <BT-117>0</BT-117>
        <BT-118>E</BT-118>
        <BT-119>0</BT-119>
        <BT-120>Exemtion reason text</BT-120>
        <BT-121>Exemption reason code</BT-121>
    </BG-23>
    <BG-24>
        <BT-122>Supporting document ref</BT-122>
        <BT-123>Supporting document descr</BT-123>
        <BT-124>External document location</BT-124>
        <BT-125 mime="application/pdf" filename="filename0">ZGVmYXVsdA==</BT-125>
    </BG-24>
    <BG-25>
        <BT-126>1a</BT-126>
        <BT-127>Invoice line note</BT-127>
        <BT-128 scheme="">Line object identifier</BT-128>
        <BT-129>10</BT-129>
        <BT-130>EA</BT-130>
        <BT-131>1000</BT-131>
        <BT-132>12345</BT-132>
        <BT-133>6789</BT-133>
        <BG-26>
            <BT-134>2018-11-12</BT-134>
            <BT-135>2018-11-30</BT-135>
        </BG-26>
        <BG-27>
            <BT-136>10</BT-136>
            <BT-137>1000</BT-137>
            <BT-138>1</BT-138>
            <BT-139>Invoice line allowance reason</BT-139>
            <BT-140>55</BT-140>
        </BG-27>
        <BG-28>
            <BT-141>10</BT-141>
            <BT-142>1000</BT-142>
            <BT-143>1</BT-143>
            <BT-144>Invoice line charge reason</BT-144>
            <BT-145>AAA</BT-145>
        </BG-28>
        <BG-29>
            <BT-146>10</BT-146>
            <BT-147>1</BT-147>
            <BT-148>11</BT-148>
            <BT-149>1</BT-149>
            <BT-150>EA</BT-150>
        </BG-29>
        <BG-30>
            <BT-151>S</BT-151>
            <BT-152>5</BT-152>
        </BG-30>
        <BG-31>
            <BT-153>Item name</BT-153>
            <BT-154>Item description</BT-154>
            <BT-155>Item seller's identifier</BT-155>
            <BT-156>Item buyer's identifier</BT-156>
            <BT-157 scheme="">Item standar identifier</BT-157>
            <BT-158 scheme="ZZZ" version="version0">Item classification identifier0</BT-158>
            <BT-159>IT</BT-159>
            <BG-32>
                <BT-160>Color</BT-160>
                <BT-161>Red</BT-161>
            </BG-32>
            <BG-32>
                <BT-160>Size</BT-160>
                <BT-161>L</BT-161>
            </BG-32>
        </BG-31>
    </BG-25>
    <BG-25>
        <BT-126>1b</BT-126>
        <BT-129>10</BT-129>
        <BT-130>EA</BT-130>
        <BT-131>1000</BT-131>
        <BG-29>
            <BT-146>10</BT-146>

        </BG-29>
        <BG-30>
            <BT-151>E</BT-151>
            <BT-152>0</BT-152>
        </BG-30>
        <BG-31>
            <BT-153>Item name 2</BT-153>
        </BG-31>
    </BG-25>
</SEMANTIC-INVOICE>
```

## 4. Do something with it

And don't forget to have fun.

Kind regards,\
Your Mustang Team\
Jochen Stärk\
Chief [Mustangproject.org](https://mustangproject.org/?mtm_campaign=b2bsamples) ZUGFeRD Amatuer\
jstaerk[at]usegroup.de