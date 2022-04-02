## PSi Docs Publishing Instructions

You must clone both the docs and pages repos in same location:  

`git clone https://github.com/product-science/docs`  
`git clone https://product-science.github.io/`  

A setup script to setting up your environment is here:  
`sh ./buildtools/mkdocs-setup.sh`

To build and deploy docs:
* in docs repo: `mkdocs build`
* in product-science.github.io repo: `sh ../docs/buildtools/io-deploy.sh`