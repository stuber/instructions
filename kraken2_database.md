# Kraken 2 custom database development

Freely available pre-built hash files [here](https://benlangmead.github.io/aws-indexes/k2)

[Kraken 2 manual](https://github.com/DerrickWood/kraken2/wiki/Manual)

Read manual.  It's Awesome!

Go to directory to install database.

```bash
DBNAME=$(pwd)
```

Install the latest and greatest taxonomy database.

```bash
kraken2-build --download-taxonomy --db $DBNAME
```

## Install standard genomic libraries

Favorites:

- archaea
- bacteria
- plasmid
- viral
- human
- fungi
- plant
- protozoa
- UniVec_Core

For example:

```bash
kraken2-build --download-library archaea --db $DBNAME
```

## Install custom genomes

Make a directory to gather genomes

```bash
mkdir ${DBNAME}/my_custom_genomes
cd ${DBNAME}/my_custom_genomes
```

RefSeq genomes can be searched [here](https://www.ncbi.nlm.nih.gov/).  Search "All Databases" in the top search bar.  For example, search "bos taurus".  NCBI will return the search results and highlight a RefSeq genome assembly.  Select the "Download" button.  Download the "Genomic FASTA" from the "RefSeq" database.  

Including these in build has worked good:

- Bos taurus (cow)
- Sus scrofa (pig)
- Equus caballus (horse)
- gallus gallus (chicken)
- Canis lupus familiaris (dog)
- Felis catus (house cat)
- Odocoileus virginianus (white-tailed deer)
- Panthera tigris altaica (Amur tiger)
- Loxodonta africana (elephant)
- Tursiops_truncatus (bottlenose dolphin)
- Anas_platyrhynchos (mallard)
- Nanorana parkeri(frog)
- Cyprinus carpio (common carp)
- Aedes albopictus (mosquito)
- Dermacentor silvarum (tick)


Once genomes are downloaded transfer, unzipped genomes to `${DBNAME}/my_custom_genomes` as `.fna` files.

When in `${DBNAME}/my_custom_genomes`:

```bash
for file in *fna; do kraken2-build --add-to-library $file --db $DBNAME; done
```

Build with available threads:

```bash
kraken2-build --build --threads 24 --db $DBNAME
```

Once built:

```bash
echo $DBNAME
```

This is your new database path for Kraken 2.

```bash
kraken2 --db ${DBNAME} --threads ${CPU_NUMBER} --paired ${read1} ${read2} --output ${sample_name}-outputkraken.txt --report ${sample_name}-reportkraken.txt
```

Finish with Krona graph

```bash
krona_lca_all.py -f ${sample_name}-outputkraken.txt
ktImportTaxonomy kronaInput.txt
mv taxonomy.krona.html ${sample_name}-taxonomy.krona.html
mv taxonomy.krona.html.files ${sample_name}-taxonomy.krona.html.files
```

## Bracken steps

"library" directory with genomes used to build Kraken2 database must be present at kraken2 database location.  Read length of 240 assuming 500 base chemistry.

Build:
```bash
bracken-build -d ${DBNAME} -t 46 -k 35 -l 240
```

Run:
```bash
bracken -d ${DBNAME} -i ${sample_name}-reportkraken.txt -o ${sample_name}-bracken.txt -r 240
```
