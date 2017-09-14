# Conda environment

## Environment creation

### Settings
#### Channels
```
# Backup your .condarc
mv ~/.condarc ~/.condarc.bk

# Set the Channels
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

### Creation
```bash
conda create --override-channels --channel bioconda --channel conda-forge --channel r -n eba2017_nom_atelier tool2==1.0.0 tool2==1.0.1
```

Example: eba2017_rnaseq_denovo
```
conda create -n eba2017_rnaseq_denovo trinity==2.4.0 kallisto==0.43.0 salmon==0.8.2 trimmomatic==0.36 fastqc==0.11.5 multiqc==0.9 bioconductor-deseq2==1.16.1 bioconductor-edger==3.16.5
```

### Exportation
```
conda env export -n eba2017_rnaseq_denovo -f eba2017_rnaseq_denovo.yaml
```

### Importation
```
conda env create -f eba2017_rnaseq_denovo.yaml -n eba2017_rnaseq_denovo
```

## Environment usage

### Admin: Facilitate the use

```
export CONDA3=/usr/local/genome2/conda3/bin
function conda3activate () { export PATH=/usr/local/genome2/conda3/bin:$PATH; }
function conda3deactivate () { export PATH=$(echo $PATH | sed "s|/usr/local/genome2/conda3/bin:||g"); }
```

### User: Usage
#### In terminal / qlogin
```
conda env list
source activate eba2017_rnaseq_denovo
```

#### Through `qsub`
```
source $CONDA3/activate eba2017_rnaseq_denovo
```
