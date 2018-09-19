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
$ grep -E "ZMMIL|ZMMLR|ZMMMR" fang_et_al_genotypes.txt > maize_genotype.txt

$ grep -E "ZMPBA|ZMPIL|ZMPJA" fang_et_al_genotypes.txt > teosinte_genotype.txt

```

* Checking the number of lines in maize or teosinte genotype files to make sure grep command worked.

```
$ wc -l maize_genotype.txt
$ wc -l teosinte_genotype.txt

```

* Extracting header line from fang_et_al_genotypes.txt


```
$ head -n 1 fang_et_al_genotypes.txt > header_genotype.txt

```

* Checking the number of lines in header file to make sure the command worked

```
$ wc -l header_genotype.txt

```


* Adding header to maize and teosinte files

```
$ cat header_genotype.txt maize_genotype.txt > maize_header_genotype.txt

$ cat header_genotype.txt teosinte_genotype.txt > teosinte_header_genotype.txt

```

* Checking the number of lines of each file to make sure that command worked

```
$ wc -l maize_header_genotype.txt

$ wc -l teosinte_header_genotype.txt

```


* Transposing maize and teosinte files from columns to rows

```
$ awk -f transpose.awk maize_header_genotype.txt > transposed_maize_genotype.txt

$ awk -f transpose.awk teosinte_header_genotype.txt > transposed_teosinte_genotype.txt

```

* Checking the 1st column to see if the file is transposed

```
$ cut -f 1 transposed_maize_genotype.txt| head -n 10 

$ cut -f 1 transposed_teosinte_genotype.txt| head -n 10
```


* Checking the number of lines in transposed maize and teosinte files

```
$ wc -l transposed_maize_genotype.txt

$ wc -l transposed_teosinte_genotype.txt

```


* Getting rid of the first three lines of the transposed maize and teosinte files

```
$ tail -n +4 transposed_maize_genotype.txt > matched_transposed_maize_genotype.txt

$ tail -n +4 transposed_teosinte_genotype.txt > matched_transposed_teosinte_genotype.txt

```

* Checking the number of lines 

```
$ wc -l matched_transposed_maize_genotype.txt

$ wc -l matched_transposed_teosinte_genotype.txt
```


* Sorting maize and teosinte by column 1 (SNP_ID)

```
$ sort -t -c -k 1 matched_transposed_maize_genotype.txt > sorted_matched_transposed_maize_genotype.txt

$ sort -k 1 matched_transposed_teosinte_genotype.txt > sorted_matched_transposed_teosinte_genotype.txt

```

* Checking the first column of sorted files

```
$ cut -f 1 sorted_matched_transposed_maize_genotype.txt |head -n 10

$ cut -f 1 sorted_matched_transposed_maize_genotype.txt |tail -n 10

$ cut -f 1 sorted_matched_transposed_teosinte_genotype.txt |head -n 10

$ cut -f 1 sorted_matched_transposed_teosinte_genotype.txt |tail -n 10
```

* Checking the number of lines of snp_position.txt

```
$ wc -l snp_position.txt

```



* Getting rid of the header of snp_position.txt to match the lines of the transposed maize and teosinte files

```
$ tail -n +2 snp_position.txt > matched_snp_position.txt

```

* Checking the number of lines of matched_snp_position.txt

```
$ wc -l matched_snp_position.txt

```

* Extracting column 1 (SNP_ID), column 3 (chromosome) and column 4 (position) from snp_position files to a new file

```
$ cut -f 1,3,4 matched_snp_position.txt > matched_3column_snp_position.txt

```


* Sorting the new file

```
$ sort -k 1 matched_3column_snp_position.txt > sorted_matched_3column_snp_position.txt

```

* Checking the first column of snp file to make sure it matched the sorted maize or teosinte files

```
$ cut -f 1 sorted_matched_3column_snp_position.txt |head -n 10

$ cut -f 1 sorted_matched_3column_snp_position.txt |tail -n 10
```

* Joining maize or teosinte files with new snp file, snp files first

```
$ join -1 1 -2 1 sorted_matched_3column_snp_position.txt sorted_matched_transposed_maize_genotype.txt > joined_maize_genotype.txt

$ join -1 1 -2 1 sorted_matched_3column_snp_position.txt sorted_matched_transposed_teosinte_genotype.txt > joined_teosinte_genotype.txt

```
* Checking the number of lines in joined files

```
$ wc -l joined_maize_genotype.txt

$ wc -l joined_teosinte_genotype.txt

```


* Extracting chromosome 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, unknown and multiple respectively to a new file from maize files

```
$ awk '$2 == 1' joined_maize_genotype.txt | sort -V -k 3 > chr1_increasing_position_maize_genotype

$ awk '$2 == 2' joined_maize_genotype.txt | sort -V -k 3 > chr2_increasing_position_maize_genotype

$ awk '$2 == 3' joined_maize_genotype.txt | sort -V -k 3 > chr3_increasing_position_maize_genotype

$ awk '$2 == 4' joined_maize_genotype.txt | sort -V -k 3 > chr4_increasing_position_maize_genotype

$ awk '$2 == 5' joined_maize_genotype.txt | sort -V -k 3 > chr5_increasing_position_maize_genotype

$ awk '$2 == 6' joined_maize_genotype.txt | sort -V -k 3 > chr6_increasing_position_maize_genotype

$ awk '$2 == 7' joined_maize_genotype.txt | sort -V -k 3 > chr7_increasing_position_maize_genotype

$ awk '$2 == 8' joined_maize_genotype.txt | sort -V -k 3 > chr8_increasing_position_maize_genotype

$ awk '$2 == 9' joined_maize_genotype.txt | sort -V -k 3 > chr9_increasing_position_maize_genotype

$ awk '$2 == 10' joined_maize_genotype.txt | sort -V -k 3 > chr10_increasing_position_maize_genotype

$ awk '$2 == "unknown"' joined_maize_genotype.txt | sort -V -k 3 > chr_unknown_increasing_position_maize_genotype

$ awk '$2 == "multiple"' joined_maize_genotype.txt | sort -V -k 3 > chr_multiple_increasing_position_maize_genotype
```

  
* Sorting each chromosome file by decreasing position (column 3) and replacing missing value ? with - in maize files

```
$ awk '$2 == 1' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr1_decreasing_position_maize_genotype

$ awk '$2 == 2' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr2_decreasing_position_maize_genotype

$ awk '$2 == 3' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr3_decreasing_position_maize_genotype

$ awk '$2 == 4' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr4_decreasing_position_maize_genotype

$ awk '$2 == 5' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr5_decreasing_position_maize_genotype

$ awk '$2 == 6' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr6_decreasing_position_maize_genotype

$ awk '$2 == 7' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr7_decreasing_position_maize_genotype

$ awk '$2 == 8' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr8_decreasing_position_maize_genotype

$ awk '$2 == 9' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr9_decreasing_position_maize_genotype

$ awk '$2 == 10' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr10_decreasing_position_maize_genotype

$ awk '$2 == "unknown"' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr_unknown_decreasing_position_maize_genotype

$ awk '$2 == "multiple"' joined_maize_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr_multiple_decreasing_position_maize_genotype


```

* Extracting chromosome 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, unknown and multiple respectively to a new file from teosinte files

```
$ awk '$2 == 1' joined_teosinte_genotype.txt | sort -V -k 3 > chr1_increasing_position_teosinte_genotype

$ awk '$2 == 2' joined_teosinte_genotype.txt | sort -V -k 3 > chr2_increasing_position_teosinte_genotype

$ awk '$2 == 3' joined_teosinte_genotype.txt | sort -V -k 3 > chr3_increasing_position_teosinte_genotype

$ awk '$2 == 4' joined_teosinte_genotype.txt | sort -V -k 3 > chr4_increasing_position_teosinte_genotype

$ awk '$2 == 5' joined_teosinte_genotype.txt | sort -V -k 3 > chr5_increasing_position_teosinte_genotype

$ awk '$2 == 6' joined_teosinte_genotype.txt | sort -V -k 3 > chr6_increasing_position_teosinte_genotype

$ awk '$2 == 7' joined_teosinte_genotype.txt | sort -V -k 3 > chr7_increasing_position_teosinte_genotype

$ awk '$2 == 8' joined_teosinte_genotype.txt | sort -V -k 3 > chr8_increasing_position_teosinte_genotype

$ awk '$2 == 9' joined_teosinte_genotype.txt | sort -V -k 3 > chr9_increasing_position_teosinte_genotype

$ awk '$2 == 10' joined_teosinte_genotype.txt | sort -V -k 3 > chr10_increasing_position_teosinte_genotype

$ awk '$2 == "unknown"' joined_teosinte_genotype.txt | sort -V -k 3 > chr_unknown_increasing_position_teosinte_genotype

$ awk '$2 == "multiple"' joined_teosinte_genotype.txt | sort -V -k 3 > chr_multiple_increasing_position_teosinte_genotype
```

  
* Sorting each chromosome file by decreasing position (column 3) and replacing missing value ? with - in teosinte files

```
$ awk '$2 == 1' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr1_decreasing_position_teosinte_genotype

$ awk '$2 == 2' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr2_decreasing_position_teosinte_genotype

$ awk '$2 == 3' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr3_decreasing_position_teosinte_genotype

$ awk '$2 == 4' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr4_decreasing_position_teosinte_genotype

$ awk '$2 == 5' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr5_decreasing_position_teosinte_genotype

$ awk '$2 == 6' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr6_decreasing_position_teosinte_genotype

$ awk '$2 == 7' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr7_decreasing_position_teosinte_genotype

$ awk '$2 == 8' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr8_decreasing_position_teosinte_genotype

$ awk '$2 == 9' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr9_decreasing_position_teosinte_genotype

$ awk '$2 == 10' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr10_decreasing_position_teosinte_genotype

$ awk '$2 == "unknown"' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr_unknown_decreasing_position_teosinte_genotype

$ awk '$2 == "multiple"' joined_teosinte_genotype.txt | sort -V -r -k 3 |sed -e 's/?/-/g' > chr_multiple_decreasing_position_teosinte_genotype


```

* Checking the order on position(column 3) for each chromosome file and missing value

```
$ awk -F " " '{print $3}' chr1_increasing_position_maize_genotype |head -n 10

$ awk -F " " '{print $3}' chr1_decreasing_position_maize_genotype |head -n 10

$ awk -F " " '{print $3}' chr1_increasing_position_teosinte_genotype |head -n 10

$ awk -F " " '{print $3}' chr1_decreasing_position_teosinte_genotype |head -n 10

```




 

