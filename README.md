# Product Science Documentation

To get started, please proceed to [Product Science Documentation Homepage](https://product-science.github.io/).


## Build

Clone repo:
```
git clone https://github.com/product-science/docs
```  

A setup script to setting up your environment is here:
```
./buildtools/mkdocs-setup.sh
```

### Run locally
To run locally you should provide Github token to access latest release:
```
export PS_GITHUB_TOKEN=ghp_...
```

Then serve on localhost:
```
mkdocs serve
```

Or if `mkdocs` is not available:
```
python3 -m mkdocs serve
```
 

### Deploy

`Deploy` CICD pileline deploys documentation automatically
