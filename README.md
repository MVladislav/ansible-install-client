# Install Client

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

Tested with:

- Ubuntu 23.04
- Ubuntu 24.04
- Ubuntu 25.04

## Role Variables

```yml
clients:
  - name: "{{ ansible_user }}"
    setup: true # if client should be setup with additional tools and gui (default true)

# ------------------------------------------------------------------------------
# application download from source, which needs to be updated manually
# also check section under "install_client_gdm_gui_setup" for manual update
# NOTE: https://www.virtualbox.org/wiki/Linux_Downloads
install_client_links_to_check_update_virtualbox: https://download.virtualbox.org/virtualbox/7.0.14/virtualbox-7.0_7.0.14-161095~Ubuntu~jammy_amd64.deb
# NOTE: https://www.veracrypt.fr/en/Downloads.html
install_client_links_to_check_update_veracrypt: https://launchpad.net/veracrypt/trunk/1.26.7/+download/veracrypt-1.26.7-Ubuntu-24.04-amd64.deb
install_client_links_to_check_update_veracrypt_cli: https://launchpad.net/veracrypt/trunk/1.26.7/+download/veracrypt-console-1.26.7-Ubuntu-24.04-amd64.deb
# NOTE: curl -s https://api.github.com/repos/brimdata/zui/releases/latest | grep "http.*\.deb" | cut -d '"' -f 4
install_client_links_to_check_update_brim: https://github.com/brimdata/zui/releases/download/v1.17.0/zui_1.17.0_amd64.deb
# NOTE: link should be latest version
install_client_links_to_check_update_portmaster: https://updates.safing.io/latest/linux_amd64/packages/portmaster-installer.deb
# NOTE: curl -s https://api.github.com/repos/logseq/logseq/releases/latest | grep "http.*\.AppImage" | cut -d '"' -f 4
install_client_links_to_check_update_logseq: https://github.com/logseq/logseq/releases/download/0.10.9/Logseq-linux-x64-0.10.9.AppImage
install_client_links_to_check_update_logseq_checksum: 5d13ae6364652a71af2b554dbf36ae1ee2c98af79754aac860fa69a33f1f0a67
# NOTE: curl -s https://api.github.com/repos/Ultimaker/Cura/releases/latest | grep "http.*linux.*\.AppImage\"" | cut -d '"' -f 4
install_client_links_tp_check_update_ultimaker: https://github.com/Ultimaker/Cura/releases/download/5.7.2-RC2/UltiMaker-Cura-5.7.2-linux-X64.AppImage
install_client_links_tp_check_update_ultimaker_checksum: 5e54dc0a622a71f4e0f1fc4cd8a0e293aeaa8c82a4b567adfbde25148256a296

install_client_config:
  # GNOME ---------------------------------
  gnome_gui_setup: false # NOTE: activates gui setup below. depends on clients[...].setup
  # gnome_gui_setup_dependencies: false
  gnome_gui_setup_extensions: false
  gnome_gui_setup_extensions_apt_ubuntu_tiling: false
  gnome_gui_setup_extensions_git_caffeine: false
  gnome_gui_setup_extensions_git_blur_shell: false
  gnome_gui_setup_extensions_git_burn_window: false
  gnome_gui_setup_extensions_git_dash_to_panel: false
  gnome_gui_setup_keybinding: false
  gnome_gui_setup_overlay: false
  gnome_terminal_setup_overlay: false
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
  apt_connections: false
  apt_virt_viewer: false
  apt_logitech_unifying_solaar: false
  apt_mpv: false
  # DPKG ----------------------------------
  dpkg_virtualbox: false
  dpkg_veracrypt: false
  dpkg_veracrypt_cli: false
  dpkg_brim: false
  dpkg_portmaster: false
  # DIST KEY ------------------------------
  distribution_key_virtualbox: false
  distribution_key_1password_cli: false
  distribution_key_tuxedo: false
  # APPIMAGE ------------------------------
  app_image_logseq: false
  app_image_ultimaker: false
  # SNAP ----------------------------------
  snap_brave: false
  snap_chromium: false
  snap_firefox: false
  snap_1password: false
  snap_keepassxc: false
  snap_yubioath: false
  snap_denaro: false
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
  snap_loupe: false
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
  snap_android_studio: false
  snap_beekeeper_studio: false
  snap_code: false
  snap_dbeaver: false
  snap_gnome_boxes: false
  snap_insomnia: false
  snap_postman: false
  snap_remmina: false
  snap_rpi_imager: false
  snap_ghidra: false
  snap_zaproxy: false
  snap_mqtt_explorer: false
  snap_UBports: false
  snap_fbreader: false
  # FLATPAK -------------------------------
  flatpak_brave: false
  flatpak_chromium: false
  flatpak_firefox: false
  flatpak_librewolf: false
  flatpak_1password: false
  flatpak_keepassxc: false
  flatpak_yubioath: false
  flatpak_denaro: false
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
  flatpak_loupe: false
  flatpak_lunacy: false
  flatpak_upscayl: false
  flatpak_amberol: false
  flatpak_haruna: false
  flatpak_showtime: false
  flatpak_totem: false
  flatpak_obs: false
  flatpak_parabolic: false
  flatpak_video_trimmer: false
  flatpak_vlc: false
  flatpak_moosync: false
  flatpak_spotify: false
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
  flatpak_extension_manager: false
  flatpak_lact: false
  flatpak_missioncenter: false
  flatpak_cryptomator: false
  flatpak_flatseal: false
  flatpak_pika_backup: false
  flatpak_anydesk: false
  flatpak_ausweisapp2: false
  flatpak_easy_effects: false
  flatpak_filezilla: false
  flatpak_logseq: false
  flatpak_papers: false
  flatpak_planify: false
  flatpak_solaar: false
  flatpak_warp: false
  flatpak_session: false
  flatpak_threemaqt: false
  flatpak_conjure: false
  flatpak_peek: false
  flatpak_ultimaker: false
  flatpak_girens: false
  flatpak_mpv: false
  flatpak_parsec: false
  flatpak_coppwr: false
  flatpak_helvum: false
  flatpak_jamesdsp: false
  flatpak_heroic: false
  flatpak_lutris: false
  flatpak_proton_up: false
  flatpak_protonplus: false
  flatpak_steam: false
  flatpak_arduinoide: false
  flatpak_betaflightconfigurator: false
  flatpak_fritzing: false
  flatpak_gnome_boxes: false
  flatpak_mongodb_compass: false
  flatpak_sublimetext: false
  flatpak_zed: false
  flatpak_connections: false
  flatpak_virt_viewer: false
  flatpak_wireshark: false
  # OTHER --------------------------------
  vs_code_ext: false # NOTE: depends on clients[...].setup
  firefox_setup: false # NOTE: will add arkenfox user.js, check it when you not want the default from git. depends on clients[...].setup
```

## App list for possible install

| App                    | snap | flathub | dpkg | dist_key | app image | apt  | topic   |
| :--------------------- | :--: | :-----: | :--: | :------: | :-------: | :--: | :------ |
| base\*                 |      |         |      |          |           |  x   | system  |
| auth_priv\*            |      |         |      |          |           |  x   | system  |
| ubuntu                 |      |         |      |          |           |  x   | system  |
| archive\*              |      |         |      |          |           |  x   | system  |
| codec\*                |      |         |      |          |           |  x   | system  |
| gnome\*                |      |         |      |          |           |  x   | system  |
| snap                   |      |         |      |          |           |  x   | system  |
| flatpak\*              |      |         |      |          |           |  x   | system  |
| texmaker               |      |         |      |          |           |  x   | office  |
| vpn_resolvconf         |      |         |      |          |           |  x   | vpn     |
| vpn_l2tp\*             |      |         |      |          |           |  x   | vpn     |
| vpn_openvpn\*          |      |         |      |          |           |  x   | vpn     |
| vpn_openconnect\*      |      |         |      |          |           |  x   | vpn     |
| vpn_wireguard          |      |         |      |          |           |  x   | vpn     |
| veracrypt              |      |         |  x   |          |           |      | secure  |
| veracrypt_cli          |      |         |  x   |          |           |      | secure  |
| virtualbox             |      |         |  x   |    x     |           |      | dev     |
| 1password_cli          |      |         |      |    x     |           |      | secure  |
| tuxedo                 |      |         |      |    x     |           |      | sys     |
| portmaster             |      |         |  x   |          |           |      | secure  |
| brim                   |      |         |  x   |          |           |      | pen     |
| brave                  |  x   |    x    |      |          |           |      | browser |
| chromium               |  x   |    x    |      |          |           |      | browser |
| firefox                |  x   |    x    |      |          |           |      | browser |
| librewolf              |      |    x    |      |          |           |      | browser |
| 1password              |  x   |    x    |      |          |           |      | secure  |
| keepassxc              |  x   |    x    |      |          |           |      | secure  |
| yubioath               |  x   |    x    |      |          |           |      | secure  |
| denaro                 |  x   |    x    |      |          |           |      | office  |
| flameshot              |      |    x    |      |          |           |      | office  |
| foliate                |  x   |    x    |      |          |           |      | office  |
| libreoffice            |  x   |    x    |      |          |           |      | office  |
| newsflash              |  x   |    x    |      |          |           |      | office  |
| okular                 |  x   |    x    |      |          |           |      | office  |
| onlyoffice             |  x   |    x    |      |          |           |      | office  |
| thunderbird            |  x   |    x    |      |          |           |      | office  |
| xournalpp              |  x   |    x    |      |          |           |      | office  |
| zoom                   |  x   |    x    |      |          |           |      | office  |
| discord                |  x   |    x    |      |          |           |      | social  |
| jdownloader            |  x   |    x    |      |          |           |      | social  |
| signal                 |  x   |    x    |      |          |           |      | social  |
| telegram               |  x   |    x    |      |          |           |      | social  |
| blender                |  x   |    x    |      |          |           |      | design  |
| darktable              |  x   |    x    |      |          |           |      | design  |
| drawio                 |  x   |    x    |      |          |           |      | design  |
| gimp                   |  x   |    x    |      |          |           |      | design  |
| inkscape               |  x   |    x    |      |          |           |      | design  |
| krita                  |  x   |    x    |      |          |           |      | design  |
| loupe                  |  xx  |    x    |      |          |           |      | design  |
| lunacy                 |  x   |    x    |      |          |           |      | design  |
| upscayl                |  x   |   xx    |      |          |           |      | design  |
| amberol                |  x   |    x    |      |          |           |      | video   |
| haruna                 |  x   |    x    |      |          |           |      | video   |
| obs                    |  x   |   xx    |      |          |           |      | video   |
| parabolic              |  x   |    x    |      |          |           |      | video   |
| video_trimmer          |  x   |    x    |      |          |           |      | video   |
| vlc                    |  x   |    x    |      |          |           |      | video   |
| moosync                |  x   |    x    |      |          |           |      | music   |
| spotify                |  x   |    x    |      |          |           |      | music   |
| android_studio         |  x   |    x    |      |          |           |      | dev     |
| beekeeper_studio       |  x   |    x    |      |          |           |      | dev     |
| code                   |  x   |    x    |      |          |           |      | dev     |
| dbeaver                |  x   |    x    |      |          |           |      | dev     |
| gnome_boxes            |  x   |    x    |      |          |           |  x   | dev     |
| insomnia               |  x   |    x    |      |          |           |      | dev     |
| postman                |  x   |    x    |      |          |           |      | dev     |
| remmina                |  x   |   xx    |      |          |           |      | dev     |
| rpi_imager             |  x   |    x    |      |          |           |      | dev     |
| ghidra                 |  x   |   xx    |      |          |           |      | pen     |
| zaproxy                |  x   |    x    |      |          |           |      | pen     |
| mqtt_explorer          |  x   |         |      |          |           |      | dev     |
| UBports                |  x   |         |      |          |           |      | dev     |
| fbreader               |  x   |         |      |          |           |      | office  |
| extension_manager      |      |   xx    |      |          |           |      | system  |
| lact                   |      |    x    |      |          |           |      | system  |
| missioncenter          |      |    x    |      |          |           |      | system  |
| cryptomator            |      |    x    |      |          |           |      | secure  |
| flatseal               |      |   xx    |      |          |           |      | secure  |
| pika_backup            |      |    x    |      |          |           |      | secure  |
| anydesk                |      |    x    |      |          |           |      | office  |
| ausweisapp2            |      |    x    |      |          |           |      | office  |
| easy_effects           |      |    x    |      |          |           |      | office  |
| filezilla              |      |    x    |      |          |           |      | office  |
| logseq                 |      |   xx    |      |          |     x     |      | office  |
| papers                 |      |    x    |      |          |           |      | office  |
| planify                |      |    x    |      |          |           |      | office  |
| solaar (logi)          |      |    x    |      |          |           |  x   | office  |
| warp                   |      |    x    |      |          |           |      | office  |
| session                |      |    x    |      |          |           |      | social  |
| threemaqt              |      |    x    |      |          |           |      | social  |
| conjure                |      |    x    |      |          |           |      | design  |
| peek                   |      |    x    |      |          |           |      | design  |
| ultimaker              |      |   xx    |      |          |     x     |      | design  |
| girens                 |      |    x    |      |          |           |      | video   |
| mpv                    |      |    x    |      |          |           |  x   | video   |
| parsec                 |      |    x    |      |          |           |      | video   |
| showtime               |      |   xx    |      |          |           |      | video   |
| totem                  |      |    x    |      |          |           |      | video   |
| coppwr                 |      |    x    |      |          |           |      | music   |
| helvum                 |      |    x    |      |          |           |      | music   |
| jamesdsp               |      |    x    |      |          |           |      | music   |
| heroic                 |      |    x    |      |          |           |      | game    |
| lutris                 |      |    x    |      |          |           |      | game    |
| proton_up              |      |    x    |      |          |           |      | game    |
| protonplus             |      |    x    |      |          |           |      | game    |
| steam                  |      |    x    |      |          |           |      | game    |
| arduinoide             |      |    x    |      |          |           |      | dev     |
| betaflightconfigurator |      |    x    |      |          |           |      | dev     |
| fritzing               |      |    x    |      |          |           |      | dev     |
| mongodb_compass        |      |    x    |      |          |           |      | dev     |
| sublimetext            |      |    x    |      |          |           |      | dev     |
| zed                    |      |    x    |      |          |           |      | dev     |
| connections            |      |    x    |      |          |           |  x   | dev     |
| virt_viewer            |      |    x    |      |          |           |  x   | dev     |
| wireshark              |      |    x    |      |          |           | TODO | pen     |

## Dependencies

Developed and testes with Ansible 2.14.4

## Example Playbook

```yml
- hosts: clients
  roles:
    - role: install_client
      clients:
        - name: "{{ ansible_user }}"
          setup: true # if client should be setup with additional tools and gui (default true)
      install_client_config: [] # see list above for example
```

## License

MIT

## Resources

- <https://github.com/arkenfox/user.js>
