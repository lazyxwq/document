## 1.将字符文件其中尾行的windows格式\r\n与unix格式的\n互相转换
&emsp;&emsp;基于 DOS/Windows 的文本文件在每一行末尾有一个 CR（回车）和 LF（换行），而 UNIX 文本只有一个换行,即win每行结尾为\r\n，而linux只有一个\n如果win下的文档上传到linux，每行的结尾都会出现一个^M，(^M是ctrl+v,ctrl+m)。  
 &emsp;&emsp;如果是单个文档的话，可以用vi打开，执行 :%s/^M//g　来去掉^M。  
 &emsp;&emsp;但如里批量去除的话就不能用vi了，  
 ### 方法１:  　
 &emsp;&emsp;用```dos2unix```工具，把win文档转换成linux下文档命令:```find ./ -type f -print0 | xargs -0 dos2unix``` 如果想把linux下的文档转换成win下的:```find ./ -type f -print0 | xargs -0 unix2dos```  
 ### 方法2: 
 &emsp;&emsp;用```sed```命令把win文档转换成linux下文档:```find ./ -type f print0 | xargs -0 sed -i 's/^M$//'``` 把linux下的文档转换成win下的```fild ./ -type f print0 | xargs -0 sed -i 's/$/^M/'```

    作者：小幕
    链接：https://www.zhihu.com/question/22130727/answer/33814375
    来源：知乎
    著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。