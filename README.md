#Vim Better Whitespace Plugin

This plugin causes all trailing whitespace characters (spaces and tabs) to be
highlighted. Whitespace for the current line will not be highlighted
while in insert mode. It is possible to disable current line highlighting while in other
modes as well (see options below). A helper function `:StripWhitespace` is also provided
to make whitespace cleaning painless.

Here is a screenshot of this plugin at work:
![Example Screenshot](http://i.imgur.com/St7yHth.png)

##Installation
There are a few ways you can go about installing this plugin:

1.  If you have [Vundle](https://github.com/gmarik/Vundle.vim) you can simply add:
    ```
    Bundle 'ntpeters/vim-better-whitespace'
    ```
    to your `.vimrc` file then run:
    ```
    :BundleInstall
    ```
2.  If you are using [Pathogen](https://github.com/tpope/vim-pathogen), you can just run the following command:
    ```
    git clone git://github.com/ntpeters/vim-better-whitespace.git ~/.vim/bundle/
    ```
3.  While this plugin can also be installed by copying its contents into your `~/.vim/` directory, I would highly recommend using one of the above methods as they make managing your Vim plugins painless.

##Usage
Whitespace highlighting is enabled by default, with a highlight color of red.

To set a custom highlight color, just call:
```
highlight ExtraWhitespace ctermbg=<desired_color>
```

To toggle whitespace highlighting on/off, call:
```
:ToggleWhitespace
```

To disable highlighting for the current line in normal mode call:
```
:CurrentLineWhitespaceOff <level>
```
Where `<level>` is either `hard` or `soft`.

The level `hard` will maintain whitespace highlighting as it is, but may
cause a slow down in Vim since it uses the CursorMoved event to detect and
exclude the current line.

The level `soft` will use syntax based highlighting, so there shouldn't be
a performance hit like with the `hard` option.  The drawback is that this
highlighting will have a lower priority and may be overwritten by higher
priority highlighting.

To re-enable highlighting for the current line in normal mode:
```
:CurrentLineWhitespaceOn
```

To clean extra whitespace, call:
```
:StripWhitespace
```
By default this operates on the entire file. To restrict the portion of
the file that it cleans, either give it a range or select a group of lines
in visual mode and then execute it.

To enable/disable stripping of extra whitespace on file save, call:
```
:ToggleStripWhitespaceOnSave
```
This will strip all trailing whitespace everytime you save the file for all file
types.  If you would prefer to only stip whitespace for certain filetypes, add
the following to your `~/.vimrc`:
```
autocmd FileType <desired_filetypes> autocmd BufWritePre <buffer> StripWhitespace
```
where `<desired_filetypes>` is a comma separated list of the file types you want
to be stripped of whitespace on file save ( ie. `javascript,c,cpp,java,html,ruby` )
Note that `<buffer>` is a keyword here and should stay just as it appears in the line above.

##Screenshots
Here are a couple more screenshots of the plugin at work.

This screenshot shows how the current line is not highlighted in insert mode:
![Insert Screenthot](http://i.imgur.com/RNHR9KX.png)

This screenshot shows the current line not being highlighted in normal mode( `CurrentLineWhitespaceOff hard` ):
![Normal Screenshot](http://i.imgur.com/o888Z7b.png)

This screenshot shows how highlighting works fine for spaces, tabs, and a mixture of both:
![Tabs Screenshot](http://i.imgur.com/bbsVRUf.png)

##Promotion
If you like this plugin, please star it on Github and vote it up at Vim.org!

Repository exists at: http://github.com/ntpeters/vim-better-whitespace

Plugin also hosted at: http://www.vim.org/scripts/script.php?script_id=4859

##Credits
Originally inspired by: https://github.com/bronson/vim-trailing-whitespace

Based on:

http://sartak.org/2011/03/end-of-line-whitespace-in-vim.html

http://vim.wikia.com/wiki/Highlight_unwanted_spaces
