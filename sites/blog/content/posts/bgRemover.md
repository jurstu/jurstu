---
date: 2025-08-27T20:18:23Z
# description: ""
# image: ""
lastmod: 2025-08-27
showTableOfContents: false
# tags: ["",]
title: "BgRemover"
type: "post"
---


So uh, I kind of like to use background removers like remove.bg.. However there is an issue with them... 

They offer limited resolution of the output image and try charging like ~1$ per full image resolution inference...

That seems un-cheap and I have the knowledge (insert Tai Lopez meme here) to build something like that for myself from ~scratch.

I recently adore NiceGUI for my projects and since this seems like a perfect use case I decided to go for it. There are a few things I have to get working together:

- [ ] nice-ish working front to be able to upload/download files
- [ ] actual background removal mechanix, but since it's python this should be doable
- [ ] host it somewhere in my infra for it to be usable

Nice to have-s:

- [ ] instead of uploading an image pass a URL 
- [ ] self-managed-file-deleting back-end
- [ ] option to select which model is used for the bgRemoval
- [ ] publically available on github to finally give back to community! 