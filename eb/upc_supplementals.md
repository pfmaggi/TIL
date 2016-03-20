# Reading barcodes with EAN Supplementals

## What is an EAN Supplementals?
EAN Supplementals are defined in [UPC documentation in Appendix D](http://web.archive.org/web/19990501035133/http://www.uc-council.org/d36-d.htm).  
You can have a 2 characters or a 5 characters supplemental encoding.  
I've seen this kind of encoding (UPC EAN supplemental5) on magazines and books.

## So what?
If you use Enterprise Browser Barcode API default configuration, you are not going to read the supplemental characters on the side of the main barcode.
You need to specify in the options that you want to read the supplementals character enabling it like in the sample below:
  
    EB.Barcode.enable({upcEanSupplemental5:true, upcEanSupplementalMode:EB.Barcode.UPCEAN_AUTO}, <callback>);
 
 In this case we're enabling 5 characters supplements.  
 For additional information you can check [Enteprise Browser documentation](http://ebzebra.github.io/docs/1.4/#api-barcode?upcEanSupplemental5).