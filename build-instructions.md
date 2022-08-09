## PSi Docs Publishing Instructions

A setup script to setting up your environment is here:  
`sh ./buildtools/mkdocs-setup.sh`

Clone both the docs and pages repos in same location:  

`git clone https://github.com/product-science/docs`  
`git clone https://github.com/product-science/product-science.github.io`  

To build and deploy docs:
* in docs repo: `mkdocs build`
* in `product-science.github.io` repo:  
```bash
sh ../docs/buildtools/io-deploy.sh
```
