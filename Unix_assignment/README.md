# BCB546X Unix Assignment
## File Inspection
* Looking at the top of the files

`head -n 1 fang_et_al_genotypes.txt > fang_et_al_genotypes.header.txt`
`cat fang_et_al_genotypes.header.txt`


`head -n 1 snp_position.txt > snp_position.header.txt`
`cat snp_position.header.txt`

* Looking at the bottom 2 lines of the fils

```
tail -n 2 fang_et_al_genotypes.txt > fang_et_al_genotypes.tail.txt

cat fang_et_al_genotypes.tail.txt

tail -n 2 snp_position.txt > snp_position.tail.txt

cat snp_position.tail.txt

```
* Looking at the number of lines, words and characters of the files

```
wc fang_et_al_genotypes.txt > fang_et_al_genotypes.wc.txt
cat fang_et_al_genotypes.wc.txt

wc snp_position.txt > snp_position.wc.txt
cat snp_position.wc.txt
```
* Looking at the file size of the files

```
ls -lh fang_et_al_genotypes.txt
du -h fang_et_al_genotypes.txt

ls -lh snp_position.txt
du -h snp_position.txt

```
* Looking at the first line of the files

```
head -n 1 fang_et_al_genotypes.txt 
head -n 1 snp_position.txt
``` 
* Looking at the last line of the files

```
tail -n 1 fang_et_al_genotypes.txt
tail -n 1 snp_position.txt

```

## Data Processing
* Extracting maize or teosinte files from fang_et_al_genotypes.txt

```
```

* Extracting header line from fang_et_al_genotypes.txt


```
```


* Adding header to maize and teosinte files

```
```


* Transposing maize and teosinte files from columns to rows

```
```


* Checking the number of lines in transposed maize and teosinte files

```
```


* Getting rid of the first three lines of the transposed maize and teosinte files

```
```


* Sorting maized and teosinte by column 1 (SNP_ID)

```
```


* Getting rid of the header of snp_position.txt to match the transposed maize and teosinte files

```
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


 

