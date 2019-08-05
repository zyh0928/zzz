## Command

```sh
# Installing specific packages
pacman -S <package_name>[{[name1][,name2..]}]

# To see what packages belong to the package_name group
pacman -Sg <package_name>

# Update all packages on the system
pacman -Syu

# Remove old packages from cache directory (-cc for all)
pacman -Scc

# To display extensive information about a given package
pacman -Si [package_name]

# Remove unneeded packages
pacman -Rs <package_name>

# Remove configuration files
pacman -Rn <package_name>

# Remove system unneeded packages
pacman -R $(pacman -Qtdq)

# For locally installed packages
pacman -Q[i] [package_name]

# To list all packages no longer required as dependencies (orphans):
pacman -Qdt
```
