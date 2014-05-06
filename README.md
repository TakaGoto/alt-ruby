alt-ruby.vim
============

Alt-ruby.vim is a lightweight Vim plugin that was developed during a hackfest to assist with finding related ruby spec and implementation files.
It is influenced by Rails.vim and Alternate.vim, but attempts to improve upon the success rate of these plugins.
For example, Rails.vim struggles to find related files that are nested deep within complicated file structures,
such as services/api/lib/app/controllers/api/v2/incentives.rb. If you attempt to find the alternate file,
Rails.vim complains that it it 'Can't find file "services/api/lib/.../incentives_test.rb" in path.'
Alt-ruby.vim is able to figure out that the alternate file you want is services/api/spec/lib/app/controllers/api/v2/incentives_spec.rb.

## Why

When your working on a software project you will often need to:

* Find and open the spec for the current implementation file.
* Find and open the implementation file for the current spec file.

## Usage

Find and open the alternate file (implementation or spec) in the current buffer:

```vim
:AlternateToggle
```

Find and open the alternate file (implementation or spec) in a new vsplit:

```vim
:AlternateVerticalSplit
```

Find and open the alternate file (implementation or spec) in a new split:

```vim
:AlternateHorizontalSplit
```

## Installation

[pathogen.vim](https://github.com/tpope/vim-pathogen) is the recommended installation method. 

    cd ~/.vim/bundle
    git clone https://github.com/clembradley/alt-ruby.git

It is also recommended that you add the following mappings to your .vimrc:

    nnoremap <leader>at :AlternateToggle<cr>
    nnoremap <leader>av :AlternateVerticalSplit<cr>
    nnoremap <leader>as :AlternateHorizontalSplit<cr>


## Recognised file patterns

### Ruby

```
app/**/foo.rb -> spec/**/foo_spec.rb
spec/**/foo_spec.rb -> app/**/foo_spec.rb

**/app/**/foo.rb -> **/spec/**/foo_spec.rb
**/spec/**/foo_spec.rb -> **/app/**/foo_spec.rb

lib/foo.rb -> spec/lib/foo_spec.rb
spec/lib/foo_spec.rb -> lib/foo.rb

lib/app/**/foo.rb -> spec/lib/app/**/foo_spec.rb
spec/lib/app/**/foo_spec.rb -> lib/app/**/foo.rb

**/lib/app/**/foo.rb -> **/spec/lib/app/**/foo_spec.rb
**/spec/lib/app/**/foo_spec.rb -> **/lib/app/**/foo.rb
```
