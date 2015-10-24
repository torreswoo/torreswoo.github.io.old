### vim
- http://vimawesome.com/?q=cscope
- http://often.tistory.com/109
### vundle
- Source Explorer
- Tag List
- NERDTree
- PowerLine
   - http://humb1ec0ding.github.io/2013/11/26/ubuntu-powerline-beautify-the-stateline.html
- Plugin 'bling/vim-airline'
- Plugin 'Valloric/YouCompleteMe'
   - brew install vim /-> ~/.bash_profile -> $PATH
   - http://nophotoplease.tistory.com/6
   - http://stackoverflow.com/questions/16174564/how-can-i-tell-git-which-vim-to-use

####
- vi ~/.vimrc
- vi ~/.bash_rc
- http://csl.skku.edu/uploads/SSE3044F12/vim_ctags_cscope.pdf
- http://hackereyes.tistory.com/198

### ctags
- PluginSearch
- 실행 : $> ctags -R

### cscope
- http://iamroot.org/wiki/doku.php?id=%EC%8A%A4%ED%84%B0%EB%94%94:cscope_%EC%82%AC%EC%9A%A9%EB%B2%95
- /usr/bin/mkcscope.sh // chmod 755 mkcscope.sh
-> 실행 : $> mkcscope.sh
```
// cscope DB생성을 편하게 하기위해서
#!/bin/sh
rm -rf cscope.files cscope.out
find . \( -name '*.c' -o -name '*.cpp' -o -name '*.cc' -o -name '*.h' -o -name '*.s' -o -name '*.S' \) -print > cscope.files  # 만약 문제가 발생한다면 <== 여기를 한라인으로 작성하길 바란다.
cscope -i cscope.files
```

```
#!/bin/sh

## Delete a cscope.files
[ "$1" = "-r" -o "$1" = "-R" ] && rm -f cscope.files > /dev/null


## Make a cscope.files
if [ ! -f cscope.files ]; then
    echo -n "Making cscope.files ......... : "
    find . \( -name .svn -o -name CVS -o -name .git \) -prune -o \
    \( -name '*.CPP' -o -name '*.cpp' -o -name '*.C' -o -name '*.c' -o -name '*.H' -o -name '*.h' -o -name '*.HPP' -o -name '*.hpp' -o -name '*.s' -o -name '*.S' \) \
    -print > cscope.files

    if [ $? = 0 ] ; then
        echo "[ OK ]"
    else
        echo "[ Failure ]"
    fi  
fi


## Exit when cscope.files size is 0
if [ ! -s cscope.files ];then
    echo "Target files are not exist."
    rm -f cscope.files
    exit 1
fi


## Delete a database files (cscope.out, tags)
if [ -f cscope.out -o -f tags ]; then
    rm -f cscope.out tags
fi


## Make a cscope.out
    echo -n "Making cscope.out ........... : "
cscope -h > /dev/null 2>&1
if [ $? -eq 0 ];then
    cscope -U -b -i cscope.files
    echo "[ OK ]"
else
    echo "[ Failure ]"
fi


## Make tags
    echo -n "Making tags ................. : "
ctags -L cscope.files
if [ $? = 0 ] ; then
    echo "[ OK ]"
else
    echo "[ Failure ]"
fi


echo "done"
```


- ~/.vim/plugin/cscope_maps.vim <== 플러그인 파일을 받아온다
