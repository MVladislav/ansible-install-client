# Install Client

---

[![Ansible Lint](https://github.com/MVladislav/ansible-install-client/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/MVladislav/ansible-install-client/actions/workflows/ansible-lint.yml)
[![Ansible Molecule Test](https://github.com/MVladislav/ansible-install-client/actions/workflows/ci.yml/badge.svg)](https://github.com/MVladislav/ansible-install-client/actions/workflows/ci.yml)

- [Install Client](#install-client)
  - [Role Variables](#role-variables)
  - [App list for possible install](#app-list-for-possible-install)
  - [Dependencies](#dependencies)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Resources](#resources)

---

You can checkout [MVladislav - ansible-env-setup - playbooks](https://github.com/MVladislav/ansible-env-setup/tree/main/playbooks) for how i use it in general.

## Role Variables

```yml
clients:
  - name: "{{ ansible_user }}"
    dev: true
    updateOrCreate: false
    setup: true # if client should be setup with additional tools and gui (default true)

# ------------------------------------------------------------------------------
# application download from source, which needs to be updated manually
# also check "install_client_fonts" and "install_client_gdm_gui_setup" for manual update
# NOTE: https://www.virtualbox.org/wiki/Linux_Downloads
install_client_links_to_check_update_virtualbox: https://download.virtualbox.org/virtualbox/7.0.14/virtualbox-7.0_7.0.14-161095~Ubuntu~jammy_amd64.deb
# NOTE: https://www.veracrypt.fr/en/Downloads.html
install_client_links_to_check_update_veracrypt: https://launchpad.net/veracrypt/trunk/1.26.7/+download/veracrypt-1.26.7-Ubuntu-23.04-amd64.deb
install_client_links_to_check_update_veracrypt_cli: https://launchpad.net/veracrypt/trunk/1.26.7/+download/veracrypt-console-1.26.7-Ubuntu-23.04-amd64.deb
# NOTE: link should be latest version
install_client_links_to_check_update_parsec: https://builds.parsecgaming.com/package/parsec-linux.deb
# NOTE: curl -s https://api.github.com/repos/brimdata/zui/releases/latest | grep "http.*\.deb" | cut -d '"' -f 4
install_client_links_to_check_update_brim: https://github.com/brimdata/zui/releases/download/v1.5.0/zui_1.5.0_amd64.deb
# NOTE: link should be latest version
install_client_links_to_check_update_portmaster: https://updates.safing.io/latest/linux_amd64/packages/portmaster-installer.deb
# NOTE: curl -s https://api.github.com/repos/logseq/logseq/releases/latest | grep "http.*\.AppImage" | cut -d '"' -f 4
install_client_links_to_check_update_logseq: https://github.com/logseq/logseq/releases/download/0.10.5/Logseq-linux-x64-0.10.5.AppImage
install_client_links_to_check_update_logseq_checksum: 17761baa0bcbd383f49d76885642650aaff3f21504d0cd14bad901b36a26b811
# NOTE: curl -s https://api.github.com/repos/Ultimaker/Cura/releases/latest | grep "http.*linux.*\.AppImage\"" | cut -d '"' -f 4
install_client_links_tp_check_update_ultimaker: https://github.com/Ultimaker/Cura/releases/download/5.6.0/UltiMaker-Cura-5.6.0-linux-X64.AppImage
install_client_links_tp_check_update_ultimaker_checksum: 107896a0da4b2873f3bfaad9aed36012bef2fff89571161e57f4da0a7f10a440

install_client_config:
  # GENERAL -------------------------------
  dev: false
  fonts_install: false
  # GNOME ---------------------------------
  gnome_gui_setup: false # general of gnome setup should be triggered, below specific what (dependencies will than general installed)
  gnome_gui_setup_dependencies: false
  gnome_gui_setup_extensions: false
  gnome_gui_setup_extensions_apt_ubuntu_tiling: false
  gnome_gui_setup_extensions_git_caffeine: false
  gnome_gui_setup_extensions_git_sound: false
  gnome_gui_setup_extensions_git_blur_shell: false
  gnome_gui_setup_extensions_git_burn_window: false
  gnome_gui_setup_extensions_git_dash_to_panel: false
  gnome_gui_setup_extensions_git_ui_tune: false
  gnome_gui_setup_keybinding: false
  gnome_gui_setup_overlay: false
  gnome_terminal_setup_overlay: false
  # cleanup_remove_snap: false
  # cleanup_remove_flatpak: false
  # APT -----------------------------------
  apt_base: false
  apt_auth_priv: false
  apt_ubuntu: false
  apt_archive: false
  apt_codec: false
  apt_gnome: false
  apt_snap: false
  apt_flatpak: false
  apt_vpn_resolvconf: false
  apt_vpn_wireguard: false
  apt_vpn_openvpn: false
  apt_vpn_openconnect: false
  apt_vpn_l2tp: false
  apt_gnome_boxes: false
  apt_texmaker: false
  apt_virt_viewer: false
  apt_logitech_unifying_solaar: false
  apt_mpv: false
  # DPKG ----------------------------------
  dpkg_virtualbox: false
  dpkg_veracrypt: false
  dpkg_veracrypt_cli: false
  dpkg_parsec: false
  dpkg_brim: false
  dpkg_portmaster: false
  # DIST KEY ------------------------------
  distribution_key_virtualbox: false
  distribution_key_1password_cli: false
  # APPIMAGE ------------------------------
  app_image_logseq: false
  app_image_ultimaker: false
  # SNAP ----------------------------------
  snap_1password: false
  snap_keepassxc: false
  snap_yubioath: false
  snap_chromium: false
  snap_denaro: false
  snap_firefox: false
  snap_flameshot: false
  snap_foliate: false
  snap_libreoffice: false
  snap_newsflash: false
  snap_okular: false
  snap_onlyoffice: false
  snap_thunderbird: false
  snap_xournalpp: false
  snap_zoom: false
  snap_discord: false
  snap_jdownloader: false
  snap_signal: false
  snap_telegram: false
  snap_blender: false
  snap_darktable: false
  snap_drawio: false
  snap_gimp: false
  snap_inkscape: false
  snap_krita: false
  snap_lunacy: false
  snap_upscayl: false
  snap_amberol: false
  snap_haruna: false
  snap_obs: false
  snap_parabolic: false
  snap_video_trimmer: false
  snap_vlc: false
  snap_moosync: false
  snap_spotify: false
  snap_steam: false
  snap_android_studio: false
  snap_beekeeper_studio: false
  snap_code: false
  snap_dbeaver: false
  snap_insomnia: false
  snap_postman: false
  snap_remmina: false
  snap_rpi_imager: false
  snap_ghidra: false
  snap_zaproxy: false
  snap_mqtt_explorer: false
  snap_UBports: false
  snap_fbreader: false
  snap_pixelfx: false
  # FLATPAK -------------------------------
  flatpak_1password: false
  flatpak_keepassxc: false
  flatpak_yubioath: false
  flatpak_chromium: false
  flatpak_denaro: false
  flatpak_firefox: false
  flatpak_flameshot: false
  flatpak_foliate: false
  flatpak_libreoffice: false
  flatpak_newsflash: false
  flatpak_okular: false
  flatpak_onlyoffice: false
  flatpak_thunderbird: false
  flatpak_xournalpp: false
  flatpak_zoom: false
  flatpak_discord: false
  flatpak_jdownloader: false
  flatpak_signal: false
  flatpak_telegram: false
  flatpak_blender: false
  flatpak_darktable: false
  flatpak_drawio: false
  flatpak_gimp: false
  flatpak_inkscape: false
  flatpak_krita: false
  flatpak_lunacy: false
  flatpak_upscayl: false
  flatpak_amberol: false
  flatpak_haruna: false
  flatpak_obs: false
  flatpak_parabolic: false
  flatpak_video_trimmer: false
  flatpak_vlc: false
  flatpak_moosync: false
  flatpak_spotify: false
  flatpak_steam: false
  flatpak_android_studio: false
  flatpak_beekeeper_studio: false
  flatpak_code: false
  flatpak_dbeaver: false
  flatpak_insomnia: false
  flatpak_postman: false
  flatpak_remmina: false
  flatpak_rpi_imager: false
  flatpak_ghidra: false
  flatpak_zaproxy: false
  flatpak_cryptomator: false
  flatpak_flatseal: false
  flatpak_ausweisapp2: false
  flatpak_easy_effects: false
  flatpak_extension_manager: false
  flatpak_filezilla: false
  flatpak_missioncenter: false
  flatpak_planify: false
  flatpak_warp: false
  flatpak_threemaqt: false
  flatpak_conjure: false
  flatpak_peek: false
  flatpak_girens: false
  flatpak_lutris: false
  flatpak_arduinoide: false
  flatpak_betaflightconfigurator: false
  flatpak_fritzing: false
  flatpak_mongodb_compass: false
  flatpak_sublimetext: false
  flatpak_wireshark: false
  # OTHER --------------------------------
  vs_code_ext: false
  firefox_setup: false # will add arkenfox user.js, check it when you not want the default from git
```

## App list for possible install

| App                      | snap | flathub | dpkg | dist_key | app image | apt  | topic  |
| :----------------------- | :--: | :-----: | :--: | :------: | :-------: | :--: | :----- |
| base\*                   |      |         |      |          |           |  x   | system |
| auth_priv\*              |      |         |      |          |           |  x   | system |
| ubuntu                   |      |         |      |          |           |  x   | system |
| archive\*                |      |         |      |          |           |  x   | system |
| codec\*                  |      |         |      |          |           |  x   | system |
| gnome\*                  |      |         |      |          |           |  x   | system |
| snap                     |      |         |      |          |           |  x   | system |
| flatpak\*                |      |         |      |          |           |  x   | system |
| texmaker                 |      |  TODO   |      |          |           |  x   | office |
| logitech_unifying_solaar |      |  TODO   |      |          |           |  x   | office |
| mpv                      |      |  TODO   |      |          |           |  x   | video  |
| vpn_resolvconf           |      |         |      |          |           |  x   | vpn    |
| vpn_l2tp\*               |      |         |      |          |           |  x   | vpn    |
| vpn_openvpn\*            |      |         |      |          |           |  x   | vpn    |
| vpn_openconnect\*        |      |         |      |          |           |  x   | vpn    |
| vpn_wireguard            |      |         |      |          |           |  x   | vpn    |
| gnome_boxes              | TODO |  TODO   |      |          |           |  x   | dev    |
| virt_viewer              |      |         |      |          |           |  x   | dev    |
| veracrypt                |      |         |  x   |          |           |      | secure |
| veracrypt_cli            |      |         |  x   |          |           |      | secure |
| virtualbox               |      |         |  x   |    x     |           |      | dev    |
| 1password_cli            |      |         |      |    x     |           |      | secure |
| portmaster               |      |         |  x   |          |           |      | secure |
| parsec                   |      |  TODO   |  x   |          |           |      | video  |
| brim                     |      |         |  x   |          |           |      | pen    |
| logseq                   | TODO |  TODO   |      |          |     x     |      | office |
| ultimaker                | TODO |  TODO   |      |          |     x     |      | design |
| 1password                |  xx  |    x    |      |          |           |      | secure |
| keepassxc                |  x   |   xx    |      |          |           |      | secure |
| yubioath                 |  x   |    x    |      |          |           |      | secure |
| chromium                 |  xx  |    x    |      |          |           |      | office |
| denaro                   |  xx  |   xx    |      |          |           |      | office |
| firefox                  |  xx  |    x    |      |          |           |      | office |
| flameshot                |  x   |   xx    |      |          |           |      | office |
| foliate                  |  xx  |   xx    |      |          |           |      | office |
| libreoffice              |  xx  |    x    |      |          |           |      | office |
| newsflash                |  x   |   xx    |      |          |           |      | office |
| okular                   |  xx  |   xx    |      |          |           |      | office |
| onlyoffice               |  xx  |    x    |      |          |           |      | office |
| thunderbird              |  xx  |   xx    |      |          |           |      | office |
| xournalpp                |  x   |    x    |      |          |           |      | office |
| zoom                     |  x   |   xx    |      |          |           |      | office |
| discord                  |  x   |    x    |      |          |           |      | social |
| jdownloader              |  x   |   xx    |      |          |           |      | social |
| signal                   |  x   |    x    |      |          |           |      | social |
| telegram                 |  x   |    x    |      |          |           |      | social |
| blender                  |  xx  |    x    |      |          |           |      | design |
| darktable                |  xx  |    x    |      |          |           |      | design |
| drawio                   |  xx  |    x    |      |          |           |      | design |
| gimp                     |  xx  |    x    |      |          |           |      | design |
| inkscape                 |  xx  |    x    |      |          |           |      | design |
| krita                    |  x   |   xx    |      |          |           |      | design |
| lunacy                   |  xx  |    x    |      |          |           |      | design |
| upscayl                  |  x   |   xx    |      |          |           |      | design |
| amberol                  |  x   |   xx    |      |          |           |      | video  |
| haruna                   |  xx  |    x    |      |          |           |      | video  |
| obs                      |  x   |   xx    |      |          |           |      | video  |
| parabolic                |  x   |   xx    |      |          |           |      | video  |
| video_trimmer            |  x   |   xx    |      |          |           |      | video  |
| vlc                      |  x   |    x    |      |          |           |      | video  |
| moosync                  |  xx  |    x    |      |          |           |      | music  |
| spotify                  |  xx  |   xx    |      |          |           |      | music  |
| steam                    |  x   |   xx    |      |          |           |      | game   |
| android_studio           |  xx  |    x    |      |          |           |      | dev    |
| beekeeper_studio         |  xx  |    x    |      |          |           |      | dev    |
| code                     |  xx  |    x    |      |          |           |      | dev    |
| dbeaver                  |  xx  |    x    |      |          |           |      | dev    |
| insomnia                 |  xx  |    x    |      |          |           |      | dev    |
| postman                  |  xx  |   xx    |      |          |           |      | dev    |
| remmina                  |  xx  |   xx    |      |          |           |      | dev    |
| rpi_imager               |  x   |    x    |      |          |           |      | dev    |
| ghidra                   |  x   |   xx    |      |          |           |      | pen    |
| zaproxy                  |  x   |   xx    |      |          |           |      | pen    |
| mqtt_explorer            |  x   |         |      |          |           |      | dev    |
| UBports                  |  x   |         |      |          |           |      | dev    |
| fbreader                 |  x   |         |      |          |           |      | office |
| pixelfx                  |  x   |         |      |          |           |      | design |
| cryptomator              |      |    x    |      |          |           |      | secure |
| flatseal                 |      |    x    |      |          |           |      | secure |
| ausweisapp2              |      |    x    |      |          |           |      | office |
| easy_effects             |      |    x    |      |          |           |      | office |
| extension_manager        |      |    x    |      |          |           |      | office |
| filezilla                |      |    x    |      |          |           |      | office |
| missioncenter            |      |    x    |      |          |           |      | office |
| planify                  |      |    x    |      |          |           |      | office |
| warp                     |      |    x    |      |          |           |      | office |
| threemaqt                |      |    x    |      |          |           |      | social |
| conjure                  |      |    x    |      |          |           |      | design |
| peek                     |      |    x    |      |          |           |      | design |
| girens                   |      |    x    |      |          |           |      | video  |
| lutris                   |      |    x    |      |          |           |      | game   |
| arduinoide               |      |    x    |      |          |           |      | dev    |
| betaflightconfigurator   |      |    x    |      |          |           |      | dev    |
| fritzing                 |      |    x    |      |          |           |      | dev    |
| mongodb_compass          |      |    x    |      |          |           |      | dev    |
| sublimetext              |      |    x    |      |          |           |      | dev    |
| wireshark                |      |    x    |      |          |           | TODO | pen    |

## Dependencies

Developed and testes with Ansible 2.14.4

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: clients
  roles:
    - role: install_client
      clients:
        - name: "{{ ansible_user }}"
          dev: true
          updateOrCreate: false
      install_client_config: [] # see list above for example
```

## License

MIT

## Resources

- <https://github.com/arkenfox/user.js>
