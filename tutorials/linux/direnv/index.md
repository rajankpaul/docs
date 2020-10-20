---
layout: default
title: direnv 
---

# Direnv

## Install

```
curl -sfL https://direnv.net/install.sh | bash
```

## Edit .bashrc
```
echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
source ~/.bashrc
```

## Create .envrc
```
echo 'layout python3' > .envrc
echo 'layout pyenv 3.6.2' > .envrc
```

[back](../)
