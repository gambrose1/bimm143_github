# Class 19: Cancer Mutation Mini-Project INFO
Gavin Ambrose PID: A18548522

## Background

To identify somatic mutations in a tumor, DNA from the tumor is
sequenced and compared to DNA from normal tissue in the same individual
using variant calling algorithms. Comparison of tumor sequences to those
from normal tissue (rather than ‘the human genome’) is important to
ensure that the detected differences are not germline mutations.

``` r
library(bio3d)
```

    Warning: package 'bio3d' was built under R version 4.4.3

``` r
Raw_data <- read.fasta("A18548522_mutant_seq.fa")
Raw_data
```

                   1        .         .         .         .         .         60 
    wt_healthy     MAKATSGAAGLRLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRDAP
    mutant_tumor   MAKATSGAAGLRLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRDAP
                   ************************************************************ 
                   1        .         .         .         .         .         60 

                  61        .         .         .         .         .         120 
    wt_healthy     EEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSVRNRGFPLLT
    mutant_tumor   EEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSVRNRGFPLLT
                   ************************************************************ 
                  61        .         .         .         .         .         120 

                 121        .         .         .         .         .         180 
    wt_healthy     VYLKVFLSPTSLREGECQWPGCARVYFSFFNTSFPACSSLKPRELCFPETRPSFRIRENR
    mutant_tumor   VYLKVFLSPTSLREGECQWPGCARVYFSFFNTSFPACSSLKPRELCFPETRPSFRIRENR
                   ************************************************************ 
                 121        .         .         .         .         .         180 

                 181        .         .         .         .         .         240 
    wt_healthy     PPGTFHQFRLLPVQFLCPNISVAYRLLEGEGLPFRCAPDSLEVSTRWALDREQREKYELV
    mutant_tumor   PPGTFHQFRLLPVQFLCPNISVAYRLLEGEGLPFRCAPDSLEVSTRWALDREQREKYELV
                   ************************************************************ 
                 181        .         .         .         .         .         240 

                 241        .         .         .         .         .         300 
    wt_healthy     AVCTVHAGAREEVVMVPFPVTVYDEDDSAPTFPAGVDTASAVVEFKRKEDTVVATLRVFD
    mutant_tumor   AVCTVHAGAREEVVMVPFPVTVYDEDDSAPTFPAGVDTASAVVEFKRKEDTVVATLRVFD
                   ************************************************************ 
                 241        .         .         .         .         .         300 

                 301        .         .         .         .         .         360 
    wt_healthy     ADVVPASGELVRRYTSTLLPGDTWAQQTFRVEHWPNETSVQANGSFVRATVHDYRLVLNR
    mutant_tumor   ADVVPASGELVRRYTSTLLPGDTWAQQTFRVEHWPNETSVQANGSFVRATVHDYRLVLNR
                   ************************************************************ 
                 301        .         .         .         .         .         360 

                 361        .         .         .         .         .         420 
    wt_healthy     NLSISENRTMQLAVLVNDSDFQGPGAGVLLLHFNVSVLPVSLHLPSTYSLSVSRRARRFA
    mutant_tumor   NLSISENRTMQLAVLVNDSDFQGPGAGVLLLHFNVSVLPVSLHLPSTYSLSVSRRARRFA
                   ************************************************************ 
                 361        .         .         .         .         .         420 

                 421        .         .         .         .         .         480 
    wt_healthy     QIGKVCVENCQAFSGINVQYKLHSSGANCSTLGVVTSAEDTSGILFVNDTKALRRPKCAE
    mutant_tumor   QIGKVCVENCQAFSGINVQYKLHSSGANCSTLGVVTSAEDTSGILFVNDTKALRRPKCAE
                   ************************************************************ 
                 421        .         .         .         .         .         480 

                 481        .         .         .         .         .         540 
    wt_healthy     LHYMVVATDQQTSRQAQAQLLVTVEGSYVAEEAGCPLSCAVSKRRLECEECGGLGSPTGR
    mutant_tumor   LHYMVVATDQQTSRQAQAQLLVTVEGSYVAEEAGCPLSCAVSKRRLECEECGGLGSPTGR
                   ************************************************************ 
                 481        .         .         .         .         .         540 

                 541        .         .         .         .         .         600 
    wt_healthy     CEWRQGDGKGITRNFSTCSPSTKTCPDGHCDVVETQDINICPQDCLRGSIVGGHEPGEPR
    mutant_tumor   CEWRQGDGKGITRNFSTCSPSTKTCPDGHCDVVETQDINICPQDCLRGSIVGGHEPGEPR
                   ************************************************************ 
                 541        .         .         .         .         .         600 

                 601        .         .         .         .         .         660 
    wt_healthy     GIKAGYGTCNCFPEEEKCFCEPEDIQDPLCDELCRTVIAAAVLFSFIVSVLLSAFCIHCY
    mutant_tumor   GIKAGYGTCNCFPEEEKCFCEPEDIQDPLCDELCRTVIAAAVLFSFIVSVLLSAFCIHCY
                   ************************************************************ 
                 601        .         .         .         .         .         660 

                 661        .         .         .         .         .         720 
    wt_healthy     HKFAHKPPISSAEMTFRRPAQAFPVSYSSSGARRPSLDSMENQVSVDAFKILEDPKWEFP
    mutant_tumor   HKFAHKPPISSAEMTFRRPAQAFPVSYSSSGARRPSLDSMENQVSVDAFKILEDPKWEFP
                   ************************************************************ 
                 661        .         .         .         .         .         720 

                 721        .         .         .         .         .         780 
    wt_healthy     RKNLVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPSELRDLLSEFNVLK
    mutant_tumor   RKNLVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPSELRDLLSEFNVLK
                   ************************************************************ 
                 721        .         .         .         .         .         780 

                 781        .         .         .         .         .         840 
    wt_healthy     QVNHPHVIKLYGACSQDGPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSSSLDH
    mutant_tumor   QVNHPHVIKLYGACSQDGPLLLIVEYAKVGSLRGFLRESRKVGPGYLGSGGSRNSSSLDH
                   **************************** ******************************* 
                 781        .         .         .         .         .         840 

                 841        .         .         .         .         .         900 
    wt_healthy     PDERALTMGDLISFAWQISQGMQYLAEMKLVHRDLAARNILVAEGRKMKISDFGLSRDVY
    mutant_tumor   PDERALTMGDLISFAWQISQGMQYLAEMKLVHRDLAARNILVAEGRKMKISDEGLSRDVY
                   **************************************************** ******* 
                 841        .         .         .         .         .         900 

                 901        .         .         .         .         .         960 
    wt_healthy     EEDSYVKRSQGRIPVKWMAIESLFDHIYTTQSDVWSFGVLLWEIVTLGGNPYPGIPPERL
    mutant_tumor   EEDSYVKRSQGRIPVKWMAIESLFDHIYTTQSDVWSFGVLLWEIVTLRGNPYPGIPYERL
                   *********************************************** ******** *** 
                 901        .         .         .         .         .         960 

                 961        .         .         .         .         .         1020 
    wt_healthy     FNLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKRRDYLDLAA
    mutant_tumor   FNLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKRRDYLDLAA
                   ************************************************************ 
                 961        .         .         .         .         .         1020 

                1021        .         .         .         .         .         1080 
    wt_healthy     STPSDSLIYDDGLSEEETPLVDCNNAPLPRALPSTWIENKLYGMSDPNWPGESPVPLTRA
    mutant_tumor   STPSDSLIYDDGLSEEETPLVDCNNAPLPRALPSTWIENKLYGMSDPNWPGESPVPLTRA
                   ************************************************************ 
                1021        .         .         .         .         .         1080 

                1081        .         .         .   1114 
    wt_healthy     DGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
    mutant_tumor   DGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
                   ********************************** 
                1081        .         .         .   1114 

    Call:
      read.fasta(file = "A18548522_mutant_seq.fa")

    Class:
      fasta

    Alignment dimensions:
      2 sequence rows; 1114 position columns (1114 non-gap, 0 gap) 

    + attr: id, ali, call

We could score residue conservation

``` r
mutation.sites <- which(conserv(Raw_data) < 1)
```

``` r
paste(Raw_data$ali[1, mutation.sites], mutation.sites, Raw_data$ali[2, mutation.sites])
```

    [1] "Y 809 V" "F 893 E" "G 948 R" "P 957 Y"

Lets get the wt sequence

Add some images

![](Alphafold%20image%20of%20TKR.png)

![](FFTMAP%20of%20RTK.png)
