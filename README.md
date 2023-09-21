# Role Name

**install client**

[![Ansible Lint](https://github.com/MVladislav/ansible-install-client/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/MVladislav/ansible-install-client/actions/workflows/ansible-lint.yml)
[![Ansible Molecule Test](https://github.com/MVladislav/ansible-install-client/actions/workflows/ci.yml/badge.svg)](https://github.com/MVladislav/ansible-install-client/actions/workflows/ci.yml)

## Requirements

_Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required._

## Role Variables

```yml
clients:
  - name: "{{ ansible_user }}"
    dev: yes
    updateOrCreate: false
    setup: true # if client should be setup with additional tools and gui (default true)

# ------------------------------------------------------------------------------
# application download from source, which needs to be updated manually
# also check "install_client_fonts" and "install_client_gdm_gui_setup" for manual update
# NOTE: https://www.virtualbox.org/wiki/Linux_Downloads
install_client_links_to_check_update_virtualbox: https://download.virtualbox.org/virtualbox/7.0.10/virtualbox-7.0_7.0.10-158379~Ubuntu~jammy_amd64.deb
# NOTE: https://www.veracrypt.fr/en/Downloads.html
install_client_links_to_check_update_veracrypt: https://launchpad.net/veracrypt/trunk/1.25.9/+download/veracrypt-1.25.9-Ubuntu-23.04-amd64.deb
install_client_links_to_check_update_veracrypt_cli: https://launchpad.net/veracrypt/trunk/1.25.9/+download/veracrypt-console-1.25.9-Ubuntu-23.04-amd64.deb
install_client_links_to_check_update_parsec: https://builds.parsecgaming.com/package/parsec-linux.deb
# NOTE: curl -s https://api.github.com/repos/brimdata/zui/releases/latest | grep "http.*\.deb" | cut -d '"' -f 4
install_client_links_to_check_update_brim: https://github.com/brimdata/zui/releases/download/v1.2.0/zui_1.2.0_amd64.deb
install_client_links_to_check_update_portmaster: https://updates.safing.io/latest/linux_amd64/packages/portmaster-installer.deb
# NOTE: curl -s https://api.github.com/repos/logseq/logseq/releases/latest | grep "http.*\.AppImage" | cut -d '"' -f 4
install_client_links_to_check_update_logseq: https://github.com/logseq/logseq/releases/download/0.9.18/Logseq-linux-x64-0.9.18.AppImage
install_client_links_to_check_update_logseq_checksum: fb6067556d2a59227f3c8637ce5d5cf6acdc3fd0d9569e84f41ec023a2ea89b1

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
  apt_latex: false
  apt_pandoc: false
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
  snap_firefox: false
  snap_chromium: false
  snap_thunderbird: false
  snap_signal_desktop: false
  snap_telegram_desktop: false
  snap_discord: false
  snap_zoom_client: false
  snap_spotify: false
  snap_libreoffice: false
  snap_onlyoffice_desktopeditors: false
  snap_fbreader: false
  snap_inkscape: false
  snap_drawio: false
  snap_gimp: false
  snap_darktable: false
  snap_pixelfx: false
  snap_upscayl: false
  snap_krita: false
  snap_lunacy: false
  snap_vlc: false
  snap_obs_studio: false
  snap_flameshot: false
  snap_1password: false
  snap_okular: false
  snap_xournalpp: false
  snap_yubioath_desktop: false
  snap_code: false
  snap_remmina: false
  snap_android_studio: false
  snap_UBports: false
  snap_insomnia: false
  snap_postman: false
  snap_dbeaver_ce: false
  snap_beekeeper_studio: false
  snap_mqtt_explorer: false
  snap_zaproxy: false
  snap_nmap: false
  snap_john_the_ripper: false
  snap_rpi_imager: false
  snap_cornyjokes: false
  snap_steam: false
  # FLATPAK -------------------------------
  flatpak_flatseal: false
  flatpak_firefox: false
  flatpak_chromium: false
  flatpak_thunderbird: false
  flatpak_newsflash: false
  flatpak_extension_manager: false
  flatpak_flameshot: false
  flatpak_onlyoffice: false
  flatpak_1password: false
  flatpak_keepassxc: false
  flatpak_cryptomator: false
  flatpak_easy_effects: false
  flatpak_signal: false
  flatpak_telegram: false
  flatpak_threemaqt: false
  flatpak_zoom: false
  flatpak_teams: false
  flatpak_discord: false
  flatpak_spotify: false
  flatpak_ferdi: false
  flatpak_vlc: false
  flatpak_amberol: false
  flatpak_haruna: false
  flatpak_warp: false
  flatpak_inkscape: false
  flatpak_drawio: false
  flatpak_gimp: false
  flatpak_conjure: false
  flatpak_krita: false
  flatpak_studio: false
  flatpak_blender: false
  flatpak_peek: false
  flatpak_video_trimmer: false
  flatpak_tube_converter: false
  flatpak_girens: false
  flatpak_code: false
  flatpak_remmina: false
  flatpak_sublimetext: false
  flatpak_arduinoide: false
  flatpak_fritzing: false
  flatpak_insomnia: false
  flatpak_postman: false
  flatpak_dbeavercommunity: false
  flatpak_mongodb_compass: false
  flatpak_filezilla: false
  flatpak_jdownloader: false
  flatpak_wireshark: false
  flatpak_ghidra: false
  flatpak_zaproxy: false
  flatpak_steam: false
  flatpak_lutris: false
  flatpak_ausweisapp2: false
  flatpak_betaflightconfigurator: false
  # OTHER --------------------------------
  vs_code_ext: false
```

## Dependencies

_A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles._

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: clients
  roles:
    - role: install_client
      clients:
        - name: "{{ ansible_user }}"
          dev: yes
          updateOrCreate: false
      install_client_config: [] # see list above for example
```

## License

GNU AFFERO GENERAL PUBLIC LICENSE

## Author Information

MVladislav
