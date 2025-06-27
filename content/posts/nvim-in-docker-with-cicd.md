---
title: "Nvim in Docker With CICD"
date: 2025-06-26T18:45:30-04:00
draft: true
---

I'm a huge fan of vim. I've been using it since 2012 and I don't predict that
changing anytime soon. I think the philosophy of vim motions -- a programming
language for moving the cursor through a text file -- is incredibly powerful. It
allows you to edit text without needing to use the mouse, which I believe is the
main bottleneck that slows us down and breaks our "flow state". Once you get the
hang of it, you feel as if you can code at the speed of your thoughts.

After using vim for a while, I wanted a way to keep my vim configuration files
in sync across my various machines. This is when I created my
[vim-config](https://github.com/rsutton1/vim-config) repo (now archived) in
2016. Now if I get a new laptop, for example, I could just pull the repo and
run a script to move my config files to the correct place.

This worked for a while, but it wasn't sufficient. Many of my vim configurations
had dependencies on various packages, which I had to track and install
manually each time I used a new computer.

That's when I made the [devbox](https://github.com/rsutton1/devbox) repo in
2022. This repo uses Github Actions to build a Docker container, which allows
both the configurations and the packages to be saved into a single image. This
means if I ever get a new laptop or start a new job, all I have to do is pull
the container and I can start coding on day one.

# Implementation

I created two repos:

1. dotfiles: static configuration files
2. devbox: pulls the configuration files and installs them into a Docker
   container.

First, I archived my vim-config repo and migrated them to the tool chezmoi.
Chezmoi is a tool for tracking static configuration files across various
devices. It provides many features more than the quick bash scripts in my
vim-config repo, which is why I decided to archive it in favor of chezmoi.

