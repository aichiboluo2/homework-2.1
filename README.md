# homework-2.1
### 查看文件行数&字数
` cd /home/test/share `<br>
`wc -l test_command.gtf `<br>
`8 test_command.gtf`<br>
`wc -c test_command.gtf`<br> 
`636 test_command.gtf`<br>
grep 'CDS' file_name       #显示匹配上 'CDS' 的所有行

grep -w 'gene' test_command.gtf    # 必须与整个字匹配 <br>
sed 's/chr_/chromosome_/g' test_command.gtf    #将文件中所有的 chr_ 替换为 chromosome_<br>

sed -n '3,6 p' file_name    #打印第3到6行

sed '2 q' file_name         #打印前2行
