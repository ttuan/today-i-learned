For a long time, I use [vim-aut-save](https://github.com/vim-scripts/vim-auto-save) to auto save in Vim. However, sometime I don't want to call `:wa` command of Vim auto save, so I google and find this command, which help auto update a file after a time:

```
set updatetime=200                                                    " Set time to auto update
au CursorHold * silent! update                                        " Update file
```
