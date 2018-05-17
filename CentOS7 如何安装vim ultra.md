1. 确定vim版本
不行就换，重新安装vim，centos本身带着的可能不适合安装ultramate vim
2. 安装ultimate vim（github上面最流行的vimrc）
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
3. 让vim替代vi：在~/.bashrc文档中加入下面命令
alias vi=vim
4. 安装个性化插件vundle
cd ~/.vim_runtime
git clone git@github.com:VundleVim/Vundle.vim.git sources_non_forked/Vundle
1. 用vundle安装其他需要的插件，需要先个性化设置一下vimrc，在ultimate vim里面，这个个性化的vimrc文档被my_configs.vim所取代，该文档有设置优先权，在这个文档里面用自己喜好的设置，在这里设置不会影响到升级
touch ~/.vim_runtime/my_configs.vim
并且写入
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

Plugin 'mattn/emmet-vim'
" emmet-vim is a vim plug-in which provides support for expanding abbreviations similar to emmet.
Plugin 'Valloric/YouCompleteMe'
" YouCompleteMe is a fast, as-you-type, fuzzy-search code completion engine for Vim. It has several completion engines


" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
安装emmet和YouCompleteMe这两个好用的插件其中YCM安装还需要一个库的支持，还需要一些设置，详细可以见他的文档，摘录一些是这样的：
 yum install cmake           (有了跳过)
yum install python-devel    (有了跳过)
yum install clang （可选，但是不用的话后面这条命令也会执行，但是过程会很慢）


cd ~/.vim/bundle/YouCompleteMe/
./install.py –all（安装所有语言库）

即可完成YCM的配置
更多可以参考：https://github.com/Valloric/YouCompleteMe
5. 其他设置
1. 升级ultimate vim
cd ~/.vim_runtime
git pull --rebase
2. 更改vim的theme为比较好用的monokai，
1. 执行下面命令
git clone git@github.com:skielbasa/vim-material-monokai.git sources_non_forked/vim-material-monokai
2. 在my_config.vim中加入配置
set background=dark
set termguicolors
colorscheme material-monokai
3. 详情参见https://github.com/ skielbasa/vim-material-monokai
3. 默认显示NERDTree...
6. 综上我的vimrc配置如下综上我的vimrc配置如下
