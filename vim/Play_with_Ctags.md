Ctags is a program which help you move to function and class, variable easily.

To use Ctags, you have to insall ctags on your ubuntu.
Run ```ctags -R .``` to generate tags file.
On vim, if you use CtrlP, you must run this command on .vimrc file:
```ctags -R```
If your vim has Ctrlp, jus do this trick: ```nnoremap <leader>.``` to your
~/.vimrc file.

