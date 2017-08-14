# filezilla-flatpak
[Flatpak](https://www.flatpak.org) that gives the user access to the [Filezilla](https://filezilla-project.org/) file transfer utilite.

Instructions:
-------------

(1) Install the flatpak repository for GNOME:
```
flatpak remote-add --from gnome https://sdk.gnome.org/gnome.flatpakrepo

```
(2) Install the required runtimes
```
  flatpak install gnome org.gnome.Sdk
  flatpak install gnome org.gnome.Platform
```
(3) Build the app from this directory:
```
flatpak-builder --force-clean --ccache --require-changes --repo=repo app org.filezillaproject.Filezilla.json
```
(4) Add a remote to your local repo and install it:
```
flatpak --user remote-add --no-gpg-verify Filezilla-repo /path/to/your/flatpak/repo
flatpak --user install filezilla-repo org.filezillaproject.Filezilla
```
(5) Run the DevApp:
```
flatpak run org.filezillaproject.Filezilla
```

Note that if you do further changes in the `appdir` (e.g. to the metadata), you'll need to re-publish it in your local repo and update before running it again:
```
flatpak build-export /path/to/your/flatpak/repo /path/to/flatpak/appdir
flatpak --user update org.filezillaproject.Filezilla
```

Last, you can bundle it to a file with the `build-bundle` subcommand:
```
flatpak build-bundle /path/to/your/flatpak/repo org.filezillaproject.Filezilla.flatpak org.filezillaproject.Filezilla
```
