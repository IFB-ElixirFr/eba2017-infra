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

eba2017_unix.yaml
```yaml
name: eba2017_unix
channels:
- bioconda
- conda-forge
- defaults
dependencies:
- bioconda::bedtools=2.26.0
- bioconda::bowtie2=2.3.2
- bioconda::fastqc=0.11.5
- bioconda::samtools=1.5
- bioconda::sickle-trim=1.33
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
#### In terminal / `qlogin`
```
conda env list
source activate eba2017_rnaseq_denovo
```

#### Through `qsub`
```
source $CONDA3/activate eba2017_rnaseq_denovo
```
