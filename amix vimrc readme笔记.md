github地址 https://github.com/amix/vimrc

# 安装
```
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
```



# 添加自己的配置

## 自己的配置：

添加 **~/.vim_runtime/my_configs.vim**文件保存自己的配置. 例如:

    	#cat ~/.vim_runtime/my_configs.vim
    	set number
    
    	"NERDTree config
    	"打开vim的时候自动打开NERDTree
    	autocmd vimenter * NERDTree
    
    	"ctags config
    	set tags=tags;
    	set autochdir



## 安装自己需要的插件

例子：通过pathogen 安装 [vim-rails](https://github.com/tpope/vim-rails)

		cd ~/.vim_runtime
		git clone git://github.com/tpope/vim-rails.git my_plugins/vim-rails

也可以不使用插件管理器安装插件(vim版本需要8+)：

​		在.vimrc文件里新增`packloadall`

​		创建打包插件的目录：

		mkdir -p ~/.vim/pack/plugins/start
​		clone想要安装的插件到目录下，例如：

		git clone --depth=1 git://github.com/maxmellon/vim-jsx-pretty  ~/.vim/pack/plugins/vim-jsx-pretty



# 快捷键映射

`<leader>` 表示 `,`  



## 普通模式

搜索

| 操作           | 快捷键           |
| :------------- | :--------------- |
| 向光标下搜索 / | `<Space>`        |
| 向光标上搜索 ? | `<Ctrl>+<Space>` |
| 取消高亮       | `<leader><cr>`   |



window间切换

                  <C-k>
        <C-h>      　　　　　<C-l>
                  <C-j>



buffer相关操作

| buffer 操作      | 快捷键       |
| :--------------- | :----------- |
| 快速保存buffer   | `<leader>w`  |
| 关闭当前buffer   | `<leader>bd` |
| 关闭所有的buffer | `<leader>ba` |



Tab相关快操作

| 操作                                     | 快捷键       | 原始cmd   |
| ---------------------------------------- | ------------ | --------- |
| 新建标签                                 | `<leader>tn` | :tabnew   |
| 仅保留当前标签页，而关闭其它所有的标签页 | `<leader>to` | :tabonly  |
| 关闭当前标签页                           | `<leader>tc` | :tabclose |
| 按照指定的次序排列标签页                 | `<leader>tm` | :tabmove  |
| 新标签页中打开当前buffer所在目录         | `<leader>te` | :tabedit  |



切换 [CWD](http://vim.wikia.com/wiki/Set_working_directory_to_the_current_file) 到当前打开buffer所在的目录: `<leader>cd`

        map <leader>cd :cd %:p:h<cr>:pwd<cr>

敲完快捷键之后的显示：
![CWD.png](https://upload-images.jianshu.io/upload_images/27136544-1ee1b8d4ffbeea1c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




| 操作                            | 快捷键       | 原始cmd |
| ------------------------------- | ------------ | ------- |
| 打开 `ack.vim` for 进行快速搜索 | `<leader>g`  | :Ack    |
| 快速打开一个空buffer            | `<leader>q`  |         |
| 打开和关闭粘贴模式              | `<leader>pp` |         |



## 可视模式

可视模式下按`*` or `#` 对当前已选中的字段进行搜索(会高亮):
先按v进入可视模式，然后按方向键选中“p”字符，然后按`*` or `#` ，即可高亮选中的字符
![visual1.png](https://upload-images.jianshu.io/upload_images/27136544-48c73f57ab54c935.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



可视视图下，先选中字符“set_nr_if_polling”，之后按`gv`，就会打开Ack.vim对选中的字符进行搜索，选中的字符
![visual2.png](https://upload-images.jianshu.io/upload_images/27136544-a49b9017a7f58b42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



可视视图下，先选中字符“set_nr_if_polling”，之后按`<leader>r` ，就可以搜索/替换选中的字符：
![visual3.png](https://upload-images.jianshu.io/upload_images/27136544-9a179e4fa4fc9261.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



vim命令行模式下：

```
:%s/old/new/g      用new替换当前文件里所有的old
```



可视视图下，先选中字符，之后按对应快捷键，可以将选用的字符用指定符号包裹起来：

| 快捷键 | 使用的字符                                   | 操作前      | 操作后        |
| ------ | ---------------------------- | ----------- | ------------- |
| $1     | ()                                           | Hello World | (Hello World) |
| $2     | []                                           | Hello World | [Hello World] |
| $3     | {}                                           | Hello World | {Hello World} |
| $$     | ""                                           | Hello World | "Hello World" |
| $q     | ''                                           | Hello World | 'Hello World' |
| $e     | &#96;&#96;|Hello World|&#96;Hello World&#96;|



## 插入模式

快速插入字符:
| 插入的内容       | 快捷键       |
| ---------------- | ------------ |
| ()               | `$1`         |
| []               | `$2`         |
| {}               | `$3`         |
| {<br>    <br/>}  | `$4`         |
| ''               | `$q`         |
| ""               | `$e`         |
| <>               | `$t` 不好使? |
| 插入当前日期时间    | 输入`xdate`  |



## 命令行模式

| 操作                                                     | 快捷键  |
| -------------------------------------------------------- | ------- |
| 命令行输入的时候，删除`/`之后的内容                      | `$q`    |
| 光标移动到输入字符的最前面(`<Home>`)                     | `<C-A>` |
| 光标移动到输入字符的最后面(`<End>`)                      | `<C-E>` |
| 清空所有的输入(`<C-U>`)                                  | `<C-K>` |
| 上一条输入的指令(`<Up>`)                                 | `<C-P>` |
| 下一条输入的指令(`<Down>`)                               | `<C-N>` |
| 通过sudo保存文件(没有权限时使用)，会把文件属组改为root？ | `:W`    |



## 插件相关的命令

### bufexplorer

打开历史文件列表以达到快速切换文件

| 操作                             | 快捷键       | 原始cmd |
| ------------------------------- | ----------- | ------- |
| 打开历史文件列表                   | `<leader>o` | :BufExplorer      |

![bufexplorer .png](https://upload-images.jianshu.io/upload_images/27136544-7697f8cfd878b52e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



### ctrlp.vim 

支持对文件、缓冲区( `:CtrlPBuffer` )、MRU(Most Recently Used)文件( `:CtrlPMRU` )和标签进行模糊搜索/查找 :

| 操作                                    | 快捷键      |
| --------------------------------------- | ----------- |
| 在当前的工作目录(CWD)查找并打开一个文件 | `<C-f> `    |
| 打开最近打开过的文件                    | `<leader>f` |
| 快速查找打开一个buffer                  | `<leader>b` |



`<C-f>`对当前CWD目录下进行搜索

![ctrlp1.png](https://upload-images.jianshu.io/upload_images/27136544-1f721b12b6fe50a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`<leader>f`最近打开过的文件:

![ctrlp2.png](https://upload-images.jianshu.io/upload_images/27136544-af1b06417b67d951.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`<leader>b` 快速查找打开一个buffer

![ctrlp3.png](https://upload-images.jianshu.io/upload_images/27136544-65c5cc4e0ae671de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



`<leader>j`快速查找打开一个文件

![ctrlp4.png](https://upload-images.jianshu.io/upload_images/27136544-64313c01e5c9d46c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



### NERDTree :

| 操作                       | 快捷键       |
| -------------------------- | ------------ |
| 打开/关闭目录树            | `<leader>nn` |
| 书签跳转                   | `<leader>nb` |
| 打开目录树并定位到当前文件 | `<leader>nf` |



### goyo.vim 和 vim-zenroom2 

把buffer居中显示，且只显示当前的一个buffer内容 (`<leader>z`)



### vim-multiple-cursors  ---TODO

多行编辑 :

    let g:multi_cursor_start_word_key      = '<C-s>'
    
    let g:multi_cursor_select_all_word_key = '<A-s>'
    
    let g:multi_cursor_start_key          = 'g<C-s>'
    
    let g:multi_cursor_select_all_key      = 'g<A-s>'
    
    let g:multi_cursor_next_key            = '<C-s>'
    
    let g:multi_cursor_prev_key            = '<C-p>'
    
    let g:multi_cursor_skip_key            = '<C-x>'
    
    let g:multi_cursor_quit_key            = '<Esc>'



### vim-yankstack :  

多次复制/删除时，把以前复制/删除的内容都缓存起来，黏贴的时候使用

    <C-p>  最新的复制/删除内容 -> 更老的内容  以此顺序黏贴
    
    <C-n>  老的复制/删除内容 -> 新的内容  以此顺序黏贴



### vim-snipmate ---TODO

自动补全插件，自定义代码片段并在以后直接黏贴 :

    ino <C-j> <C-r>=snipMate#TriggerSnippet()<cr>
    
    snor <C-j> <esc>i<right><C-r>=snipMate#TriggerSnippet()<cr>



### vim-surround---TODO

 高效操作与括号、引号或html、xml标签相关的配对符号   ---TODO:

    vmap Si S(i_<esc>f)
    
    au FileType mako vmap Si S"i${ _(<esc>2f"a) }<esc>



### ale 

实时监测代码正确性 :

    nmap <silent> <leader>a <Plug>(ale_next_wrap)



### vim-indent-guides ---TODO

显示缩进线 

    You can also use the following commands inside Vim:
    
    :IndentGuidesEnable
    
    :IndentGuidesDisable
    
    :IndentGuidesToggle



## 拼写检查

开启拼写检查  `<leader>ss`
| 操作                                 | 快捷键       | 原始cmd |
| ------------------------------------ | ------------ | ------- |
| 跳到下一处拼写错误                   | `<leader>sn` | ]s      |
| 跳到上一处拼写错误                   | `<leader>sp` | `[s`    |
| 把当前单词添加到拼写文件中           | `<leader>sa` | zg      |
| 为当前单词提供更正建议               | `<leader>s?` | z=      |
| 把当前单词从拼写文件中删除           |              | zw      |
| 撤销针对当前单词的 `zg` 或 `zw` 命令 |              | zug     |



## Cope

cope       									打开一个窗口显示当前的错误列表。                         



当使用`Ack.vim`搜索的时候，可以在cope中显示搜索结果：  `<leader>cc`

光标定位到下一个搜索结果:    `<leader>n`

光标定位到上一个搜索结果:    `<leader>p`



Cope mappings:

    map <leader>cc :botright cope<cr>
    
    map <leader>co ggVGy:tabnew<cr>:set syntax=qf<cr>pgg
    
    map <leader>n :cn<cr>
    
    map <leader>p :cp<cr>



# 卸载

- Remove `~/.vim_runtime`
- Remove any lines that reference `.vim_runtime` in your `~/.vimrc`




# 遇到的问题

1 ack不可用

    sudo apt-get install ack

2  perl: warning: Falling back to the standard locale ("C")

    Add the following lines to your bashrc or bash_profile file on the host machine:
    export LC_CTYPE=en_US.UTF-8
    export LC_ALL=en_US.UTF-8