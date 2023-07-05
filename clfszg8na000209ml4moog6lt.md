---
title: "Code formatting in Neovim"
datePublished: Wed Mar 29 2023 01:02:58 GMT+0000 (Coordinated Universal Time)
cuid: clfszg8na000209ml4moog6lt
slug: code-formatting-in-neovim
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/g5jpH62pwes/upload/d1663f5fa9c125e7d20e3285e72b5950.jpeg
tags: vim, neovim, typescript, eslint

---

As simple as it sound code formatting can get very complecated when you need to do it accross different filetype. I'm not a big fan of auto formatting on save, I like to choose when to format my code. But the problem with code formatting is there a multiple tools to do it depending on the file type.

## Here are 3 ways of code formating I have to use currently.

### For projects/files using LSP (with nvim-lsp client)

For these projects I have to use `vim.lsp.buf.format` command to format the buffer.

### For projects/files using Es lint (i.e Typescripts, Javascript, etc)

Above mentioned `vim.lsp.buf.format` does some formatting for these, but it's not enough, for these files I use \`:EslintFixAll\` command for code formatting. What it does as the name suggests it fixes all the linting issues while also formatting the code. (if you are using prettier this might be the place to use prettier too, but I think `eslint-config-prettier` plugin should handle it through this too.

### Any other files

For file that does not fall into any of those categories I use `=` to format the selection. I have a small function that does do this for the whole file and return the cursor back to where it was.

```bash
local format_buffer = function()
  local pline = vim.fn.line('.')
  local pcol = vim.fn.col('.')
  vim.cmd("normal! gg=G")
  vim.cmd("normal! " .. pline .. "G")
  vim.cmd("normal! 0")

  for i = 0, pcol, 1
  do
    vim.cmd("normal! l")
  end
  vim.cmd("normal! zz")
end
```

## One keybinding to do all of these?

So the problem with having multiple methods to format buffers makes it complicated to, because you need to call different functions for different filetypes. I created a function that abstracts all the above detaail and do the proper format command for the current filetype.

```sql
-- ~/.config/nvim/after/plugin/format.lua
local table_has = function(tbl, val)
  for _, v in ipairs(tbl) do
    if v == val then
      return true
    end
  end
  return false
end

local js_filetypes = { "javascript", "typescript", "typescriptreact", "javascriptreact", "javascript.jsx",
    "javascript.tsx", "javascript.ts", "typescript.tsx", "typescript.ts" }

vim.keymap.set('n', '<leader>cf', function()
  if vim.lsp.buf.server_ready() then
    local ft = vim.bo.filetype;
    if table_has(js_filetypes, ft) then
      local success = pcall(function()
            vim.cmd('EslintFixAll')
            print("Formatted with EslintFixAll")
          end)
      if not success then
        vim.lsp.buf.format()
        print("Formatted with LSP")
      end
    else
      vim.lsp.buf.format()
      print("Formatted with LSP")
    end
  else
    require "bmax.util".format_buffer() -- the format buffer function mentioned on the previous code example
    print("Formatted with gg=G")
  end
end)
```