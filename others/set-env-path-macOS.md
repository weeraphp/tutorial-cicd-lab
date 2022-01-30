# Set Environent Path on MacOS

## on .bash_profile

open terminal then following code below via create .bash_profile

```bash
cd ~/
touch .bash_profile
```

or if exist open .bash_profile via text editor | alternative can use vi, nano or others

```bash
open -e ~/.bash_profile
```

edit command export into bash_profile then save

```bash
export PATH=$PATH:/usr/local/bin
```

## on zshrc

```bash
open -e ~/.zshrc
```

edit command export into zshrc then save

```bash
export PATH=$PATH:/usr/local/bin
```