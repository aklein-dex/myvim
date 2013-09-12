My Vim
=====

J'utilise VIM et voici mon repository avec les submodules.
Je me suis aide de ce site:
http://mirnazim.org/writings/vim-plugins-i-use/

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


