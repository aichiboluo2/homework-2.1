# homework-2.1
### 查看文件行数&字数
` cd /home/test/share `<br>
`wc -l test_command.gtf `<br>
`8 test_command.gtf`<br>
`wc -c test_command.gtf`<br> 
`636 test_command.gtf`<br>
### 输出示例文件中以chr_起始，并且基因id为YDL248W的行
`grep '^chr_.*YDL248W' test_command.gtf`<br>      
```chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";
chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";
```

### 将示例文件中的 chr_ 替换为 chromosome_ 并输出每行的第1，3，4，5列
`sed 's/chr_/chromosome_/' test_command.gtf | awk '{print $1,$3, $4,$5}'`
```chromosome_IV gene 1802 2953
chromosome_IV transcript 802 2953
chromosome_IV exon 1802 2953
chromosome_IV CDS 1802 950
chromosome_IV start_codon 1802 1804
chromosome_IV stop_codon 2951 2953
chromosome_IV gene 762 3836
chromosome_IV transcript 3762 836
```
### 尝试互换示例文件的第2列和第3列，并且对输出结果利用 sort 命令依照第4和第5列数字大小排序，将最终结果输出到result.gtf文件中

`awk '{temp=$2;$2=$3;$3=temp; print}' test_command.gtf | sort -k4,5n > result.gtf`<br>
`cat result.gtf`
```chromosome_IV gene ensembl 762 3836 . + . gene_id "YDL247W-A"; gene_version "1";
chr_IV transcript ensembl 802 2953 . + . gene_id "YDL248W"; gene_version "1";
chr_IV gene ensembl 1802 2953 . + . gene_id "YDL248W"; gene_version "1";
chr_IV start_codon ensembl 1802 1804 . + 0 gene_id "YDL248W"; gene_version "1";
chromosome_IV CDS ensembl 1802 950 . + 0 gene_id "YDL248W"; gene_version "1";
chromosome_IV exon ensembl 1802 2953 . + . gene_id "YDL248W"; gene_version "1";
chromosome_IV stop_codon ensembl 2951 2953 . + 0 gene_id "YDL248W"; gene_version "1";
chr_IV transcript ensembl 3762 836 . + . gene_id "YDL247W-A"; gene_version "1";
```
### 更改示例文件的权限，使得文件所有者及所在用户组用户可读、写、执行而其他用户只可读，展示权限修改前后的权限变化
`ls -hl test_command.gtf`
`-rwxrwxrwx 1 root root 636 Sep 19 08:26 test_command.gtf`

`chmod 774 test_command.gtf`
`-rwxrwxr 1 root root 636 Sep 25 23:26 test_command.gtf`
