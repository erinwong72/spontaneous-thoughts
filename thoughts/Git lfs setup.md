# Git lfs setup

1. Install it onto your os:

Mac:
```bash
brew install git-lfs
```

Linux:
```
sudo apt install git-lfs
```

2. Set up git lfs in your repo
```
git lfs install
```

3. Add large file extensions for tracking
```
git-lfs track "*.extension*"
```

5. Add .gitattributes file and commit