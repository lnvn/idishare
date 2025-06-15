+++
searchHidden = true
+++

searchHidden will hide your post from search result

### Prerequisite when clone to new folder
```
$ git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
$ git submodule update --init --recursive
```

### Update submodules
```
$ git submodule update --remote --merge
```

### Hugo framework command
#### 1. Create new site
```
$ hugo new site quickstart
```

#### 2. Add content
```
$ hugo new content content/posts/my-first-post.md
```

#### 3. Start Hugo developer server
```
$ hugo server --config config.yaml
```

#### 4. Public site / Generate Html code
```
hugo --config config.yaml
```

### Thanks to
```
https://app.lottiefiles.com/
```

### README configuration
```
**my link**: [link](https://link.com)
```