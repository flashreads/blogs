---
id: 009-how-to-create-terminal-aliases
title: How to create terminal aliases
tags: 
    - alias
    - terminal
    - code editor
date: 2021-10-24 22:02:00 +0200 
keywords: alias, terminal, code editor
categories: 
    - other
author: VasekS
meta-description: How to create terminal aliases
cover: ../../images/categories/other.png
---

# What is an Alias

Aliases are nothing more than keyboard shortcuts or abbreviations, and although they’re a bit limited, they’re great for simple commands.

# Alias Structure

1. alias
2. shortcut name
3. =
4. ‘your_command’

# How to Create a Permanent Alias in the Text Editor (Sublime)

Open a terminal of your choice and insert this command which will open the bash profile in Sublime Editor: subl ~/.bash_profile

# Alias Examples

```sh
alias c=’clear’
alias gp=’git pull’
alias gs=’git status’

```
# Save Changes

Once you have created the alias(es), restart the terminaln to save/apply these changes