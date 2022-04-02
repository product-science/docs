Publishing Instructions

You must clone both the docs and pages repos in same location:  

`git clone https://github.com/product-science/docs`  
`git clone https://product-science.github.io/`  

Mkdocs must be installed: [Mkdocs install instructions](https://www.mkdocs.org/getting-started/)  

To build and deploy docs:
* in docs repo: `mkdocs build`
* in product-science.github.io repo: `mkdocs gh-deploy --config-file ../docs/mkdocs.yml --remote-branch master`