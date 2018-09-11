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

## Data Processing

 

