# VADR - Viral Annotation DefineR <a name="top"></a>
#### Version 1.0.4; March 2020
#### https://github.com/nawrockie/vadr.git

VADR is a suite of tools for classifying and analyzing sequences
homologous to a set of reference models of viral genomes or gene
families. It has been mainly tested for analysis of Norovirus and
Dengue virus sequences in preparation for submission to the GenBank
database. 

The VADR `v-annotate.pl` script is used to classify a sequence, by
determining which in a set of reference models it is most similar
to, and then annotate that sequence based on that most similar model.
Example usage of `v-annotate.pl` can be found [here](documentation/annotate.md#top).
Another VADR script, `v-build.pl`, is used to create the models from
NCBI RefSeq sequences or from input multiple sequence alignments,
potentially with secondary structure annotation. `v-build.pl` stores
the RefSeq feature annotation in the model, and `v-annotate.pl` maps
that annotation (e.g. CDS coordinates) onto the sequences it
annotates.  VADR includes 197 prebuilt models of *Flaviviridae* and
*Caliciviridae* viral RefSeq genomes, described
[here](documentation/build.md#1.0library).  Example usage of `v-build.pl` can be
found [here](documentation/build.md#top).

`v-annotate.pl` identifies unexpected or divergent attributes of the
sequences it annotates (e.g. invalid or early stop codons in CDS
features) and reports them to the user in the form of *alerts*.  A
subset of alerts are *fatal* and cause a sequence to *fail*. A
sequence *passes* if zero fatal alerts are reported for it.  VADR is
used by GenBank staff to evaluate incoming sequence submissions of
some viruses (currently Norovirus and Dengue virus).  Submitted
sequences that pass `v-annotate.pl` are accepted into GenBank.

The homology search and alignment components of VADR scripts, the most
computationally expensive steps, are performed by the Infernal and
BLAST software packages, which are downloaded and installed with [VADR
installation](documentation/install.md#top).

---
## Available VADR models <a name="models"></a>

You can download pre-built models to use to validate and
annotate viruses or cox1 genes as listed below. ***Importantly***,
to use a set of models other than the default set that is
installed with VADR, you will need to use use the `-m`, `-i` and
`-b` options as described [here](documentation/build.md#building-a-vadr-model-library).

Pre-built models are available for:
  * Norovirus and Dengue virus RefSeqs, along with other
    *Flaviviridae* and *Caliciviridae* RefSeqs (**this is the "default"
    set of models that is installed with VADR**)
  * *Coronaviridae* RefSeqs, including 2019-nCoV [(NC_045512)](https://www.ncbi.nlm.nih.gov/nuccore/NC_045512.2/)
  * metazoan Cytochrome c oxidase I (COX1)

See [this page](https://github.com/nawrockie/vadr/wiki/Available-VADR-model-files) for more information

---
## VADR documentation <a name="documentation"></a>

* [VADR installation instructions](documentation/install.md#top)
  * [Installation using `vadr-install.sh`](documentation/install.md#install)
  * [Setting environment variables](documentation/install.md#environment)
  * [Verifying successful installation](documentation/install.md#tests)
  * [Further information](documentation/install.md#further)
* [`v-build.pl` example usage and command-line options](documentation/build.md#top)
  * [`v-build.pl` example usage](documentation/build.md#exampleusage)
  * [`v-build.pl` command-line options](documentation/build.md#options)
  * [Building a VADR model library](documentation/build.md#library)
  * [How the VADR 1.0 model library was constructed](documentation/build.md#1.0library)
* [`v-annotate.pl` example usage, command-line options and alert information](documentation/annotate.md#top)
  * [`v-annotate.pl` example usage](documentation/annotate.md#exampleusage)
  * [`v-annotate.pl` command-line options](documentation/annotate.md#options)
  * [Basic Information on `v-annotate.pl` alerts](documentation/annotate.md#alerts)
  * [Additional information on `v-annotate.pl` alerts](documentation/annotate.md#alerts2)
* [VADR output file formats](documentation/formats.md#top)
  * [VADR output files created by all VADR scripts](documentation/formats.md#generic)
  * [`v-build.pl` output files](documentation/formats.md#build)
  * [`v-annotate.pl` output files](documentation/formats.md#annotate)
  * [VADR `coords` coordinate string format](documentation/formats.md#coords)
  * [VADR sequence naming conventions](documentation/formats.md#seqnames)
* [Available VADR model files](https://github.com/nawrockie/vadr/wiki/Available-VADR-model-files)

---
## Reference <a name="reference"></a>
* The recommended citation for using VADR is:
  Alejandro A Schaffer, Eneida L Hatcher, Linda Yankie, Lara
  Shonkwiler, J Rodney Brister, Ilene Karsch-Mizrachi, Eric P
  Nawrocki; *VADR: validation and annotation of virus sequence
  submissions to GenBank*;
  bioRxiv 852657; doi: https://doi.org/10.1101/852657.

---
#### Questions, comments or feature requests? Send a mail to eric.nawrocki@nih.gov.
