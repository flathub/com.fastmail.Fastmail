# com.fastmail.Fastmail (beta)

## Install

```bash
flatpak remote-add --if-not-exists flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo
flatpak install flathub-beta com.fastmail.Fastmail
```

You may have both stable and beta installed on your machine. Please refer to
[Flathub's documentation](https://docs.flathub.org/docs/for-users/installation#flathub-beta-repository)
on how to do this.

## Build

### Setup

Install `flatpak` if your distro doesn't include it.

https://flatpak.org/setup/

```bash
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install -y flathub org.flatpak.Builder
```

### Before publishing a new update

**Lint metadata manifest**

```bash
flatpak run --command=flatpak-builder-lint org.flatpak.Builder appstream com.fastmail.Fastmail.metainfo.xml
```

**Create build**

```bash
flatpak-builder --force-clean --user --install-deps-from=flathub --repo=repo --install builddir com.fastmail.Fastmail.yml
```

**Preview store listing**

```bash
gnome-software --show-metainfo com.fastmail.Fastmail.metainfo.xml
```
