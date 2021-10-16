## VIM

### window

上下分屏  :sp 

左右分屏  :vsp    或者   Ctrl +w + v

 

### Buffer

列出所有的缓冲区  :ls  :files

切换下一个缓冲区，显示下一个文件的内容 :bn

切换上一个缓冲区，显示上一个文件的内容  :bp

切换到指定缓冲区  :b number




### tab

显示已打开标签页的列表  :tabs

移动到下一个标签页：

        :tabn
        gt
        Ctrl-PgDn

移动到上一个标签页：

        :tabp
        gT
        Ctrl-PgUp



## NREDTree

### NERDTree常用快捷键

        ctrl + w + w ：光标自动在左右侧窗口切换
        t ：在新 Tab 中打开选中文件/书签，并跳到新 Tab
        T ：在新 Tab 中打开选中文件/书签，但不跳到新 Tab
        P ：跳到根结点
        p ：跳到父结点
        q ：关闭 NerdTree 窗口
        x ：收起该节点的父节点
        X ：收起该节点及所有下面的的子节点
        r ：刷新当前文件件和子文件
        R ：刷线整个目录
### 书签

        给当前选中的路径创建一个书签 :  Bookmark [<name书签名>]
        清除书签 :  ClearBookmarks [<bookmarks>]
        清除所有书签 :  ClearAllBookmarks 
        编辑书签 :  EditBookmarks 



## ctags

生成代码标签信息并实现跳转

生成tags的命令

    ctags -R *

.vimrc新增的配置

    set tags=tags;
    set autochdir

vim首先在当前目录里寻找tags文件，如果没有找到tags文件，或者没有找到对应的目标，就到父目录中查找，一直向上递归


| 操作                                       |       快捷键        |
| -----------------------------------------  |    --------------   |
| 跳转到光标所在变量、宏、函数的定义处       | **Ctrl + ]**        |
| 分割当前窗口，并在新窗口中显示跳转到的定义 | **Ctrl + W + ]**    |
| 返回到跳转前的位置                         | **Ctrl + T**        |
| 返回之前的位置                             | **Ctrl + O**        |
| 列出所有匹配的标签                         | **:ts**             |
| 跳转到指定的tag                            | **:tag  tagname**   |
|分割当前窗口，并且跳转到指定的tag           | **:stag  tagname**  | 

使用tag命令时，可以输入部分tag名，然后使用Tab键进行补全。



## ack.vim

全局搜索某个单词

搜索：

    :Ack xxx

QuickFix窗口的快捷键

| **按键** | **功能**                                |
| -------- | --------------------------------------- |
| ?        | 显示键盘映射                            |
| o        | 打开文件                                |
| O        | 打开文件关闭QuickFix窗口                |
| go       | 预览文件，但焦点留在ack搜索结果上       |
| t        | 在新标签页打开文件                      |
| T        | 在新标签页打开但不切换到那个标签页      |
| h        | 分屏打开                                |
| H        | 分屏打开，但焦点停留在ack搜索结果上     |
| v        | 竖直分屏打开                            |
| gv       | 竖直分屏打开，但焦点停留在ack搜索结果上 |
| q        | 关闭QuickFix窗口，切换到这个串口之后按q |

​    

## 安装插件vim-airline 和 vim-bufferline

```
cd ~/..vim_runtime
git clone git@github.com:vim-airline/vim-airline.git my_plugins/vim-airline
git clone git@github.com:bling/vim-bufferline.git my_plugins/vim-bufferline
```

.vimrc新增配置

```
gc@GC:~/.vim_runtime$ cat my_configs.vim
set number

"NERDTree config
"打开vim的时候自动打开NERDTree
autocmd vimenter * NERDTree

"ctags config
set tags=tags;
set autochdir

" 80 characters line
set colorcolumn=81
"execute "set colorcolumn=" . join(range(81,335), ',')
highlight ColorColumn ctermbg=black ctermfg=DarkRed

" Airline
let g:airline#extensions#tabline#enabled = 1 " Enable the list of buffers
let g:airline#extensions#tabline#fnamemod = ':t' " Show just the filename

" NERDTree
let g:NERDTreeWinPos = "left"
```



跳转到下一个buffer   `<leader>l`

跳转到前一个buffer   `<leader>h`





## cscope

http://cscope.sourceforge.net/

a:  查找此符号的赋值
c:  查找调用此函数的函数
d:  查找此函数调用的函数
e:  找到这个 egrep 模式
f:  找到这个文件
g:  找到这个定义
i:   查找文件#包括这个文件
s:  找到这个C符号
t:  查找此文本字符串 




```
 173 """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
 174 " => Text, tab and indent related
 175 """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
 176 " Use spaces instead of tabs
 177 " set expandtab
 178
 179 " Be smart when using tabs ;)
 180 set smarttab
 181
 182 " 1 tab == 8 spaces
 183 set shiftwidth=8
 184 set tabstop=8
```





