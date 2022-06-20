# macfuse-pkg
Creates Automated Releases from https://github.com/osxfuse/osxfuse as pkg

# References
https://askubuntu.com/questions/38112/how-can-i-open-a-dmg-file

## Usage?
Download from Releases Tab

```
installer -pkg Install\ macFUSE.pkg -target /Applications
```

#### Install the dmg directly?

```
sudo hdiutil attach <image>.dmg
sudo installer -package /Volumes/<image>/<image>.pkg -target /
sudo hdiutil detach /Volumes/<image>.

<image>.app instead of <image>.pkg after doing sudo hdiutil attach <image>.dmg,
you usally can just drag/copy it to /Applications

```



## How? To Do it With StealifyOS

```
sudo su -
apt-get -y install dmg2img
dmg2img ~/macfuse-4.4.0.dmg /tmp/dmg && rm -f ~/macfuse-4.4.0.dmg
mount -o loop -t hfsplus /tmp/dmg/macfuse-4.4.0.dmg /mnt/dmg
tar czf ~/macfuse-4.4.0.tar.gz /mnt/dmg
unmount /mnt/dmg
```

## Later Improvments
Reduce the installer files to license and only the needed pkg use xar to find out the true

```
apt-get install build-essential libxml2-dev libssl1.0-dev zlib1g-dev

wget https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/xar/xar-1.5.2.tar.gz
tar -zxvf xar-1.5.2.tar.gz

cd xar-1.5.2
./configure
make
make install

xar -xvf package_installer.pkg
```
