# Installing Typescript Compiler

```bash
# First install nodejs and npm.
sudo pacman -S nodejs npm

# Then install typescript, not 'tsc'.
sudo npm install --global typescript

# Don't do this.
sudo npm install -g tsc
```

Don't install `tsc` because tsc is a deprecated version of the typescript compiler.

---
