# BCB546X Unix Assignment
## File Inspection
* Looking at the top of the files

```
$ head -n 1 fang_et_al_genotypes.txt
 
$ head -n 1 snp_position.txt > snp_position.header.txt
```

* Looking at the bottom 2 lines of the fils

```
$ tail -n 2 fang_et_al_genotypes.txt 

$ tail -n 2 snp_position.txt 


```
* Looking at the number of lines, words and characters of the files

```
$ wc fang_et_al_genotypes.txt 

$ wc snp_position.txt 
```
* Looking at the file size of the files

```
$ ls -lh fang_et_al_genotypes.txt

$ du -h fang_et_al_genotypes.txt

$ ls -lh snp_position.txt

$ du -h snp_position.txt
```

## Data Processing
* Extracting maize or teosinte files from fang_et_al_genotypes.txt

```
$ grep -i "ZMMIL,ZMMLR, ZMMMR" fang_et_al_genotypes.txt > teosinte_genotype.txt

$ grep -i "ZMPBA,ZMPIL, ZMPJA" fang_et_al_genotypes.txt > teosinte_genotype.txt

```

* Extracting header line from fang_et_al_genotypes.txt


```
$ head -n 1 fang_et_al_genotypes.txt > header_genotype.txt

```


* Adding header to maize and teosinte files

```
$ cat header_genotype.txt maize_genotype.txt > maize_header_genotype.txt

$ cat header_genotype.txt teosinte_genotype.txt > teosinte_header_genotype.txt

```


* Transposing maize and teosinte files from columns to rows

```
$ awk -f transpose.awk maize_header_genotype.txt > transposed_maize_genotype.txt

$ awk -f transpose.awk teosinte_header_genotype.txt > transposed_teosinte_genotype.txt

```


* Checking the number of lines in transposed maize and teosinte files

```
$ wc -l transposed_maize_genotype.txt

$ wc -l transposed_teosinte_genotype.txt

```


* Getting rid of the first three lines of the transposed maize and teosinte files

```
$ tail -n +4 tansposed_maize_genotype.txt > matched_transposed_maize_genotype.txt

$ tail -n +4 tansposed_teosinte_genotype.txt > matched_transposed_teosinte_genotype.txt

```


* Sorting maized and teosinte by column 1 (SNP_ID)

```
$ sort -k 1 matched_transposed_maize_genotype.txt > sorted_matched_transposed_maize_genotype.txt

$ sort -k 1 matched_transposed_teosinte_genotype.txt > sorted_matched_transposed_teosinte_genotype.txt


```


* Getting rid of the header of snp_position.txt to match the transposed maize and teosinte files

```
$ tail -n +2 

```


* Extracting column 1 (SNP_ID), column 3 (chromosome) and column 4 (position) from snp_position files to a new file

```


```


* Sorting the new file

```


```


* Joining maize or teosinte files with new snp file, snp files first

```


```


* Extracting chromosome 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, unknown and multiple respectively to a new file from maize and teosinte files

```


```

  
* Sorting each chromosome file by increasing position (column 3)

```


```


* Sorting each chromosome file by decreasing position (column 3)

```


```


* Replacing "?" with "-" for each decreasing position chromosome file

```


```


 

