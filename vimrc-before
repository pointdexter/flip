set shiftwidth=4 softtabstop=4
set nocompatible
set nu
set autoindent
set ruler
set history=1000
set virtualedit=onemore 	   	" allow for cursor beyond last character
set showmode                    	" display the current mode
set rtp^=$MYPATH                                        " When I close a tab, remove the buffer
set nohidden
                                        " This shows what you are typing as a command.  I love this!
set showcmd
set  nocp
call pathogen#infect()
call pathogen#helptags()
call pathogen#runtime_append_all_bundles()
syntax on
filetype plugin indent on
filetype plugin on
set nocp
if version >= 600
  filetype plugin indent on
endif

"Since I use linux, I want this
" let g:clipbrdDefaultReg = '+'
" map <C-j> <C-W>j
" map <C-k> <C-W>k
" map <C-h> <C-W>h
" map <C-l> <C-W>l
" vmap <C-c> py
" nmap <C-c> pyiw
" vmap <C-p> pp
" nmap <C-p> pP
" imap <C-p> <Esc>ppa

" This is totally awesome - remap jj to escape in insert mode.  You'll never
" type jj anyway, so it's great!
inoremap jj <Esc>

" Tell vim to remember certain things when we exit
"  '10  :  marks will be remembered for up to 10 previously edited files
"  "100 :  will save up to 100 lines for each register
"  :20  :  up to 20 lines of command-line history will be remembered
"  %    :  saves and restores the buffer list
"  n... :  where to save the viminfo files
set viminfo='10,\"100,:20,%,n~/.viminfo

function! ResCur()
  if line("'\"") <= line("$")
    normal! g`"
    return 1
  endif
endfunction

augroup resCur
  autocmd!
  autocmd BufWinEnter * call ResCur()
augroup END
"RESTORE CURSOR TO FILE POSITION IN PREVIOUS EDITING SESSION this function
"above is connected to line 46 http://vim.wikia.com/wiki/Restore_cursor_to_file_position_in_previous_editing_session

" New Tab
nnoremap <silent> <C-t> :tabnew<CR>

"  searching
set incsearch                 " incremental search
set ignorecase                " search ignoring case
set hlsearch                  " highlight the search
set showmatch                 " show matching bracket


" Switch window mappings
 nnoremap <A-Up> :normal <c-r>=SwitchWindow('+')<CR><CR>
 nnoremap <A-Down> :normal <c-r>=SwitchWindow('-')<CR><CR>
 nnoremap <A-Left> :normal <c-r>=SwitchWindow('<')<CR><CR>
 nnoremap <A-Right> :normal <c-r>=SwitchWindow('>')<CR><CR>

"  maps NERDTree to F10

 map <silent> <F9> :NERDTreeToggle<CR>
 map! <silent> <F9> <ESC>:NERDTreeToggle<CR>

" Ctrl-L clears the highlight from the last search
 noremap <C-l> :nohlsearch<CR><C-l>
 noremap! <C-l> <ESC>:nohlsearch<CR><C-l>

" I use VIM split Windows - and I don't like navigating amongst them with
" Ctrl-w h/j/k/l. I want to use Ctrl+cursorsKeys. I also want to instantly
" close any window with Ctrl-F12:

 noremap <silent> <C-Down> <C-W>j
 noremap <silent> <C-Up> <C-W>k
 noremap <silent> <C-Left> <C-W>h
 noremap <silent> <C-Right> <C-W>l
 noremap <silent> <C-F12> :bd!<CR>

 "this is how you enter numbers"
 nmap <CR> G

"Faster shortcut for commenting. /c
map <leader>c <c-_> <c-_>


"BUFFERS
map <F3> :bnext<CR>
map <F2> :bprevious<CR>
map <F4> :BufOnly<CR> "Close all other buffers but this one
map <F5> :BufOnly<CR>:bd <cr> "Close all buffers




runtime ftplugin/man.vim

" by holding down the shift key and using the arrows you resize your window
nnoremap <S-Up> :normal <c-r>=Resize('+')<CR><CR>
nnoremap <S-Down> :normal <c-r>=Resize('-')<CR><CR>
nnoremap <S-Left> :normal <c-r>=Resize('<')<CR><CR>
nnoremap <S-Right> :normal <c-r>=Resize('>')<CR><CR>
function! Resize(dir)
  let this = winnr()
  if '+' == a:dir || '-' == a:dir
    execute "normal \<c-w>k"
    let up = winnr()
    if up != this
      execute "normal \<c-w>j"
      let x = 'bottom'
    else
      let x = 'top'
    endif
  elseif '>' == a:dir || '<' == a:dir
    execute "normal \<c-w>h"
    let left = winnr()
    if left != this
      execute "normal \<c-w>l"
      let x = 'right'
    else
      let x = 'left'
    endif
  endif
  if ('+' == a:dir && 'bottom' == x) || ('-' == a:dir && 'top' == x)
    return "5\<c-v>\<c-w>+"
  elseif ('-' == a:dir && 'bottom' == x) || ('+' == a:dir && 'top' == x)
    return "5\<c-v>\<c-w>-"
  elseif ('<' == a:dir && 'left' == x) || ('>' == a:dir && 'right' == x)
    return "5\<c-v>\<c-w><"
  elseif ('>' == a:dir && 'left' == x) || ('<' == a:dir && 'right' == x)
    return "5\<c-v>\<c-w>>"
  else
    echo "oops. check your ~/.vimrc"
    return ""
  endif
endfunction




 let mapleader = ","
nmap <leader>v :tabedit $MYVIMRC<CR>


" Automatically cd into the directory that the file is in
autocmd BufEnter * execute "chdir ".escape(expand("%:p:h"), ' ')


" Remove any trailing whitespace that is in the file
autocmd BufRead,BufWrite * if ! &bin | silent! %s/\s\+$//ge | endif

:ab #b /************************************************
:ab #e ************************************************/
:ab #l /*----------------------------------------------*/
