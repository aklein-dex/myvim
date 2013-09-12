My Vim
=====

J'utilise VIM et voici mon repository avec les submodules.
Je me suis aide de ce site:
http://mirnazim.org/writings/vim-plugins-i-use/

```
sudo apt-get install vim-nox
sudo apt-get install vim-rails

cd ~/.vim
$ git clone git://github.com/tpope/vim-pathogen.git pathogen
$ mv pathogen/autoload ~/.vim/autoload

$ cd .vim
$ git init
$ git add .
$ git commit -m "Initial commit"

$ sudo aptitude install ruby ruby-dev
$ git submodule add git://git.wincent.com/command-t.git bundle/command-t
$ git submodule init && git submodule update
$ cd ~/.vim/bundle/command-t/ruby/command-t/
$ ruby extconf.rb
$ make

$ git submodule add git://github.com/Raimondi/delimitMate.git bundle/delmitmate
$ git submodule init && git submodule update

$ git submodule add  git://github.com/altercation/vim-colors-solarized.git bundle/solarized
$ git submodule init && git submodule update

```
Mon fichier .vimrc

=====
```
call pathogen#infect()

syntax on
filetype plugin indent on
let mapleader = ","
nnoremap <silent> <Leader>t :CommandT<CR>
nnoremap <silent> <Leader>O <Esc>:CommandTFlush<CR>
let g:CommandTMaxHeight=6
colorscheme morning
set number " to show the line number
set tabstop=2 shiftwidth=2 softtabstop=2 " a tab is two spaces (or set this to 4)
set expandtab " use spaces, not tabs (optional)
set guifont=Menlo

inoremap <Up> <NOP>
inoremap <Down> <NOP>
inoremap <Left> <NOP>
inoremap <Right> <NOP>
noremap <Up> <NOP>
noremap <Down> <NOP>
noremap <Left> <NOP>
noremap <Right> <NOP>

augroup BgHighlight
  autocmd!
  autocmd WinEnter * set number
  autocmd WinLeave * set nonumber
augroup END

au BufRead,BufNewFile *.scss set filetype=scss
```

Mon fichier .bash_profile ou .bashrc
=====
```
[[ -s "/Users/alex/.rvm/scripts/rvm" ]] && source "/Users/alex/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"
# extract current git branch
function parse_git_branch
{
  branch=$(git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/')
  if [ "$branch" != "" ]; then
    echo "${branch}";
  fi
}

# custom prompt with git branch
if [ $(tput colors) == "256" ]; then
  PS1="\[\033[38;5;125m\]\w\[\033[0;34m\]\$(parse_git_branch) \[\033[0;0m\]\$ "
else
  PS1="\[\033[1;35m\]\w\[\033[1;34m\]\$(parse_git_branch) \[\033[0;0m\]\$ "
fi

```
apres executer cette commande pour reload bash:
. ~/.bash_profile


