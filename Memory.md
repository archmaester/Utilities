# Memory related utilities

## Free up apt-cache (Safe)

```
du -sh /var/cache/apt/archives
sudo apt-get clean
```

## Free up pip cache (Safe)
```
pip cache purge
```

## Free up conda old packages and cache
```
conda clean all
```
or 
```
conda clean -t
```
or 
```
conda clean -p
```
