# Human-tissues-mappings
Ontology annotation of all tissues included in [Expression Atlas][1] baseline experiments and mappings to organs.

## Human tissues
The subset of tissues included in baseline expression experiments in Expression Atlas can be retrieved from the file `assaygroupsdetails.tsv` at `/ebi/ftp/pub/databases/microarray/data/atlas/experiments/` using the following:
```
grep 'organism part' $ATLAS_EXPS/assaygroupsdetails.tsv | grep factor | awk -F"\t" '{print $5}' | sort | uniq
```
The file `human_tissues.txt` contains only the subset of human tissues included in baseline expression experiments in Expression Atlas.

## Annotation of human tissues to ontologies
Each of the human tissues included in baseline expression experiments in Expression Atlas is annotated to ontology terms using [Zooma][2], developed by the [Samples, Phenotypes and Ontologies Team][3] at [EMBL-EBI][4].

## Mapping human tissues to organs
Each of the human tissues included in baseline expression experiments in Expression Atlas has been manually mapped to organs based on the hierarchy of [Uber-anatomy ontology, UBERON][5] when possible.

Let's explain as an example the process followed to map **adrenal gland** to organs in the `EAbaseline-tissues_to_organs.txt` file. According to UBERON, adrenal gland is associated to **endocrine gland**:

organ id|organ name|tisue id|tissue name|
|-|-|-|-|
|UBERON_0002368|endocrine gland|UBERON_0002369|adrenal gland|

According to UBERON, adrenal gland can be also associated to gland. However, we have decided to map that tissue only to endocrine gland as we thought this would be more meaningful.

Some tissues, e.g. **adipose tissue**, **aorta** or **artery** cannot be mapped to any organ using UBERON. We have assigned an organ for those tissues by manual curation. 

As part of the curation process, we have defined a list of organs that has been used to map all human tissues included in baseline expression experiments in Expression Atlas in the `list_of_organs.txt` file.
 
[1]: https://www.ebi.ac.uk/gxa/home
[2]: https://www.ebi.ac.uk/spot/zooma/
[3]: https://www.ebi.ac.uk/about/spot-team
[4]: https://www.ebi.ac.uk/
[5]: http://purl.obolibrary.org/obo/uberon.owl
