# Simplifying Vim: 95% of my Vim Usage

I've been using Vim for a decade now, and over the years, I've gradually streamlined my usage to a minimalistic subset of its powerful features. While Vim can seem intimidating to newcomers, I've found that the 80-20 principle applies here as well. By focusing on a handful of essential features and a few select plugins, you can become highly productive with this amazing software. In this blog post, I'll share my minimalist Vim setup, including the plugins I use, my key combinations, and some handy commands.

## My Essential Vim Plugins

### 1. vim-gitgutter
[vim-gitgutter](https://github.com/airblade/vim-gitgutter) is a lightweight Git gutter plugin that provides a clear visual indication of changes in your Git repository directly in your code.

### 2. CtrlP
[CtrlP](https://github.com/ctrlpvim/ctrlp.vim) simplifies file navigation with its fuzzy file finder. I've configured it with a custom command to search for Git-tracked files.

```vim
let g:ctrlp_user_command = ['.git', 'cd %s && git ls-files -co --exclude-standard']
```

### 3. Nerdtree
[Nerdtree](https://github.com/preservim/nerdtree) is a file system explorer that helps you navigate your project directory easily.

### 4. vim-airline
[vim-airline](https://github.com/vim-airline/vim-airline) provides a sleek status bar at the bottom of your Vim window. Note that it requires [nerd-fonts](https://github.com/ryanoasis/nerd-fonts) for full functionality, but if you're using zsh with a theme like spaceship, you might already have these fonts installed.

## My Vim Configuration

Here's a glimpse of my Vim configuration:

```vim
syntax on
set mouse+=a
set hlsearch cursorline incsearch nu
set termguicolors
set background=dark
set expandtab tabstop=2 shiftwidth=2
set autoindent smartindent
set splitright splitbelow

call plug#begin()
  Plug 'vim-airline/vim-airline'
  Plug 'ctrlpvim/ctrlp.vim'
  Plug 'airblade/vim-gitgutter'
  Plug 'preservim/nerdtree'
call plug#end()

let g:airline_powerline_fonts = 1

let g:ctrlp_custom_ignore = '\v[\/]\.(git|hg|svn)$'
let g:ctrlp_user_command = ['.git', 'cd %s && git ls-files -co --exclude-standard']
let g:ctrlp_working_path_mode = 'ra'

nnoremap <C-\> :NERDTreeToggle<CR>
nnoremap <C-f> :NERDTreeFind<CR>
let g:NERDTreeShowHidden=1
let NERDTreeIgnore=['\.swp$']
```

## My Minimalist Key Combinations

I've deliberately kept my Vim keybindings simple. Here are the key combinations I use regularly:

- **I don't use tabs anymore:** I prefer working with splits.
- **I've stopped using bufsearch:** Simplified my workflow by using CtrlP.
- **I use arrow keys for movement:** While some Vim purists may prefer hjkl, I find arrow keys more intuitive.
- **Ctrl-w:** Switch to window mode.
- **/:** Search within the current file.
- **Ctrl-x:** CtrlP shortcut for opening a file with horizontal split.
- **Ctrl-v:** CtrlP shortcut for opening a file with vertical split.
- **i:** Enter insert mode.
- **Ctrl-c or Esc:** Return to normal mode.
- **Ctrl-p:** Trigger CtrlP.
- **Ctrl-p in insert mode:** Search for word completion.
- **n:** Go to the next searched word.
- **Ctrl-o:** Go to the previous position.
- **Ctrl-i:** Go to the next position.
- **vaw:** Select the word under the cursor.
- **caw:** Edit the word under the cursor (also copies it).
- **Shift-D:** Delete from the cursor position to the end of the line.
- **yy:** Copy the entire line.
- **dd:** Delete the entire line (also copies it).
- **p:** Paste after the cursor.
- **Shift-P:** Paste before the cursor.
- **o:** Start a new line below and enter insert mode.
- **Shift-O:** Same as 'o,' but for a line above.
- **Shift->>:** Indent the current line to the right.
- **Shift-<<:** Indent the current line to the left.
- **Shift-V:** Select the entire line.
- **gg=G:** Autoindent the entire file.

## Handy Vim Commands

Here are some Vim commands I use almost daily (I really don't I use much else):

- **:e:** Open files outside the current folder, e.g., `:e ~/.zshrc`.
- **:wqa:** Save all and quit Vim.
- **:wa:** Save all open buffers.
- **:noh:** Clear search highlights.

## Terminal Integration

For tasks that fall outside of Vim's scope, I often turn to the terminal:

- **ctrl-z:** Minimize Vim (puts it in the background), allowing me to run terminal commands.
- **fg:** Return to Vim when done with terminal commands.
- **grep -ril:** Search for a phrase throughout the project.
- **git:** Utilize Git shortcuts from my zsh Git plugin, which provides a variety of helpful commands.

Simplifying your Vim workflow can make it more approachable and productive. By focusing on essential features and plugins, you can harness the power of Vim without feeling overwhelmed by its extensive capabilities. Remember, Vim is a highly customizable editor, so feel free to adapt these tips to suit your preferences and workflow. Happy Vimming!
