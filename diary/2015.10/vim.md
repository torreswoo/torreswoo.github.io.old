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


### Python
- http://pythoninreal.blogspot.kr/2013/12/vim-python.html
```
1. Tab 설정 및 Syntax Color 설정
- http://www.vim.org/scripts/script.php?script_id=790 사이트에서 python.vim 파일을 다운로드 받아 ~/.vim/syntax/ 폴더에 복사
- ~/.vimrc 파일에는 아래와 같이 추가
syntax on
filetype plugin indent on

- Tab 설정은 ~/.vim/ftplugin/python.vim 파일에 아래와 같이 추가
set tabstop=8
set softtabstop=4
set shiftwidth=4
set textwidth=100
set expandtab
set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class
set nocindent

2. Tagging 및 소스코드 브라우징
- ctags -R 을 실행
- tagging 정보에는 클래스와 함수만 포함되는 것이 코드 브라우징을 사용하기 수월합니다. 이를 위해 ~/.ctags 파일에 아래와 같은 내용을 추가
--python-kinds=-iv
--exclude=build
--exclude=dist

3. Auto Completion 기능 : jedi-vim
- https://github.com/davidhalter/jedi-vim
- cd ~/.vim/bundle/ && git clone --recursive https://github.com/davidhalter/jedi-vim.git
- vim => PluginList & PluginInstall
```
