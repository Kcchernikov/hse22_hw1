# hse22_hw1

### Домашнее задание 1

### Код

#### 1. Подготовка данных, создание выборки
```bash
ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq

seqtk sample -s327 oil_R1.fastq 5000000 > sub1.fastq
seqtk sample -s327 oil_R2.fastq 5000000 > sub2.fastq
seqtk sample -s327 oilMP_S4_L001_R1_001.fastq 1500000 > sub1MP.fastq
seqtk sample -s327 oilMP_S4_L001_R2_001.fastq 1500000 > sub2MP.fastq
```
#### 2. Оценка качества и получение статистики при помощи fastQC и multiQC

```bash
mkdir fastqc
ls sub* | xargs -P 4 -tI{} fastqc -o fastqc {}

mkdir multiqc
multiqc -o multiqc fastqc
```
