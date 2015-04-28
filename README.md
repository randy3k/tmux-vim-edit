TmuxVimEdit: tell vim over tmux to jump
===

Inspired by the Python script [synctex-tmux-vim](https://github.com/goerz/synctex-tmux-vim). While `synctex-tmux-vim` requires `python` and `psutil`, TmuxVimEdit requires only `bash`.

### Installation

Edit your `.vimrc` and add:


```vim
function! TmuxVimEdit(file, line)
    let cfile = expand("%:p")
    if cfile == a:file
        normal! gg
        call cursor(a:line, 0)
        normal! zz
    endif
endfunction
```

Download `tmux-vim-edit` script:


```bash
curl -o /usr/local/bin/tmux-vim-edit https://raw.githubusercontent.com/randy3k/tmux-vim-edit/master/tmux-vim-edit
sudo chmod +x /usr/local/bin/tmux-vim-edit
```

### Example Usage

On terminal window 1, open a `tmux` and run `vim ~/.vimrc` on top of it. Then, open another terminal window, and run

```bash
tmux-vim-edit ~/.vimrc 20
```
the vim document on window 1 will jump to line 20!


### Skim Backward Sync from pdf to LaTeX via synctex

Open Skim -> Preferences, under the Sync tab choose Preset: Custom, put

```
/usr/local/bin/tmux-vim-edit
```
in the "Command" fieild and put

```
"%file" %line
```
in the "Arguments" field.