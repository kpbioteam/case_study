Compared to genetic studies EWAS provides a unique opportunity to study dynamic response to treatment. It has been suggested that DNA methylation is associated with drug resistance. To validate our suite we have performed analysis of differentially-methylated regions using publicly available data from the Infinium Human Methylation BeadChip array of melanoma biopsies pre and post MAPKi treatment, obtained from the Gene Expression Omnibus (GEO) (GSE65183). Methylation profiling by genome tiling array in melanoma can help us understand how non-genomic and immune changes can have an impact on treatment efficiency and disease progression. Raw image IDAT files were loaded into the Galaxy environment using Data Libraries. 

EWAS workflow was run collections of patient-matched melanoma tumours biopsied before therapy and during disease progression. The IDAT files, pre-defined phenotype tables and up-to-date genome tables (UCSC Main on Human hg19 Methyl450) were used as inputs. In order to detect poorly performing samples we ran quality diagnostics. Differentially-methylated loci were identified using single probe analysis implemented by our tool with the following parameters: phenotype set as  categorical and qCutoff size set to 0.05. The bump hunting algorithm was applied to identify  DMRs with maximum location gap parameter set to 250, genomic profile above the cutoff equal to 0.1, number of resamples set to 0, null method set to permutation and verbose equal FALSE which means that no additional progress information will be printed. Differentially-Methylated Regions and Positions revealed the need for further investigation of tissue diversity in response to environmental changes.

> We have run **Infinium Human Methylation BeadChip** {% icon tool %} with the following parameters:
>    - {% icon param-files %} *"red channel files"*: all files ending in `_Red`
>    - {% icon param-files %} *"green channel files"*: all files ending in `Grn`
>    - *"maxGap Size"*:`250`
>    We use the default gap of 250 base pairs (bps), i.e. any two points more than 250 bps away are put in a new cluster.
>    - *"Cutoff Size"*:`0.1`
>    In order to find segments that are positive, near zero, and negative. We need a cutoff which is one number in which case “near zero” default 0.1
> Default value 0 for permutation method apply selection of randomized cases with replacement from the original data while using 'bootstrap' method.
>    - *"nullMethod"*:`permutation`
> Method used to generate null candidate regions, must be one of ‘bootstrap’ or
‘permutation’ (defaults to ‘permutation’).
>    - *"Phenotype Type"*:`categorical`
> Identify regions where methylation is associated with a continuous or categorical phenotype.
>    - *"qCutoff Size"*:`0.05` 
> Diffrentialy methylated positions with an FDR q-value greater than this value will not be returned.
>    - *"Variance Shrinkage"*:` TRUE` 
> Default TRUE as it is recommended when sample sizes are small <10
>    - *"Genome Table"*: `wgEncodeHaibMethyl450 
