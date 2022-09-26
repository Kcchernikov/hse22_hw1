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
#### 3. С помощью программ platanus_trim и platanus_internal_trim подрезка чтения по качеству и удаление адаптеров

```bash
platanus_trim sub1.fastq sub2.fastq
platanus_internal_trim sub1MP.fastq sub2MP.fastq
```
#### 4. Удаление исходных .fastq файлы и полученных с помощью программы seqtk

```bash
rm oil*
rm sub1.fastq sub2.fastq sub1MP.fastq sub2MP.fastq
```
#### 5. Оценка качества подрезанных чтений и получение статистики при помощи fastQC и multiQC

```bash
mkdir fastqc_trimmed
ls sub* | xargs -P 4 -tI{} fastqc -o fastqc_trimmed {}

mkdir multiqc_trimmed
multiqc -o multiqc_trimmed fastqc_trimmed
```
