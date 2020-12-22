# Artha_flatpak
Artha is a wordnet based excellent dictionary, based on Gtk 2 and wordnet 3.0.
Artha starts crasing in Fedora 33, so I made this flatpak.
first time I've made a GTK2 application in flatpak manifest. Adwaita gtk2 theme is also included in teh flatpak using gnome-themes-extra package.

#### install flathub repo and gnome sdk 3.38
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.gnome.Sdk/x86_64/3.38

```

#### clone and build flatpak from yaml
```
git clone https://github.com/fastrizwaan/Artha_flatpak.git
cd Artha_flatpak

# build
flatpak-builder --force-clean build-dir net.sourceforge.Artha.yaml

# install 
flatpak-builder --user --install --force-clean build-dir net.sourceforge.Artha.yaml

# run
flatpak run net.sourceforge.Artha
```

#### Build a flatpak bundle file from the above built repo:
```
flatpak-builder --repo="repo" --force-clean "build" net.sourceforge.Artha.yaml
flatpak --user remote-add --no-gpg-verify "scite" "repo"
flatpak build-bundle "repo" "Artha.flatpak" net.sourceforge.Artha  --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"

flatpak --user install Artha.flatpak
flatpak run net.sourceforge.Artha
```
