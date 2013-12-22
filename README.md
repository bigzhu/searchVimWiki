# 背景 
vimwiki什么都好,就是缺少对 wiki 词的快速查找.

比如在 wikidpad 中,我可以ctrl+o,输入*bigzhu*的话,那么会将所有含有*bigzhu*的 Wiki 词都显示出来.方便我快速检索.

可是 vimwiki 没有这个功能,只有 VimwikiGoto 必须要精确匹配,用起来很不顺手.而且文章积累多了以后,像我好几k,能够让你慢的抓狂.
#python
因为懒,直接用python来实现,测试和调试都好弄.
#安装
## 程序
search_vimwiki.py 放在`/home/bigzhu/Dropbox/python/`

那么.bash_profile加入
`
export PATH=/home/bigzhu/Dropbox/python/:$PATH
`
#.vimrc修改
加入

    "search
    autocmd FileType wiki map <f4> :SearchWiki 
    
    "找 wiki 词 
    function! SearchWiki(Name)
        execute "!search_vimwiki.py '".a:Name."'"
        execute "VimwikiGoto search"
    endfunction
    autocmd FileType wiki command! -buffer -nargs=1 SearchWiki call SearchWiki("<args>")
