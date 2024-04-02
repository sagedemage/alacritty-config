# Install Alacritty from Source

Clone alacritty repository
```
git clone https://github.com/alacritty/alacritty.git
cd alacritty
```

Checkout to the latest version of Alacritty
```
git checkout tags/v0.13.2
```

Dependencies for Ubuntu
```
sudo apt install cmake pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3
```

Building on Linux
```
cargo build --release
```

Install Alacritty terminfo
```
sudo tic -xe alacritty,alacritty-direct extra/alacritty.info
```

If it returns no errors, Alacritty terminfo is already installed 
```
infocmp alacritty
```

Install desktop entry
```
sudo cp target/release/alacritty /usr/local/bin
sudo cp extra/logo/alacritty-term.svg /usr/share/pixmaps/Alacritty.svg
sudo desktop-file-install extra/linux/Alacritty.desktop
sudo update-desktop-database
```
Install manual page for Alacritty with scdoc and gzip
```
sudo apt install scdoc gzip
sudo mkdir -p /usr/local/share/man/man1
sudo mkdir -p /usr/local/share/man/man5
scdoc < extra/man/alacritty.1.scd | gzip -c | sudo tee /usr/local/share/man/man1/alacritty.1.gz > /dev/null
scdoc < extra/man/alacritty-msg.1.scd | gzip -c | sudo tee /usr/local/share/man/man1/alacritty-msg.1.gz > /dev/null
scdoc < extra/man/alacritty.5.scd | gzip -c | sudo tee /usr/local/share/man/man5/alacritty.5.gz > /dev/null
scdoc < extra/man/alacritty-bindings.5.scd | gzip -c | sudo tee /usr/local/share/man/man5/alacritty-bindings.5.gz > /dev/null
```



