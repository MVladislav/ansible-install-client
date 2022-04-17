# Role Name

_A brief description of the role goes here._

## Requirements

_Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required._

## Role Variables

```yml
install_client_service_name: default-client
install_client_config:
  # GENERAL -------------------------------
  dev: no
  fonts: no
  # GNOME ---------------------------------
  gnome_gui_setup: no # general of gnome setup should be triggered, below specific what (dependencies will than general installed)
  gnome_gui_setup_theme: no
  gnome_gui_setup_dependencies: no
  gnome_gui_setup_extensions: no
  gnome_gui_setup_keybinding: no
  gnome_gui_setup_overlay: no
  # APT -----------------------------------
  apt_base: no
  apt_base2: no
  apt_snap: no
  apt_flatpak: no
  apt_peek: no
  apt_wireshark: no
  apt_wireshark_dev: no
  apt_vpn: no
  apt_gnome_boxes: no
  apt_latex: no
  apt_pandoc: no
  apt_virt_viewer: no
  # DPKG ----------------------------------
  # dpkg_virtualbox: no
  dpkg_mongodb: no
  dpkg_veracrypt: no
  # DIST KEY ------------------------------
  distribution_key_virtualbox: no
  # SNAP ----------------------------------
  snap_chromium: no
  snap_thunderbird: no
  snap_libreoffice: no
  snap_onlyoffice_desktopeditors: no
  snap_signal_desktop: no
  snap_telegram_desktop: no
  snap_zoom_client: no
  snap_spotify: no
  snap_inkscape: no
  snap_drawio: no
  snap_gimp: no
  snap_darktable: false
  snap_vlc: no
  snap_obs_studio: no
  snap_flameshot: no
  snap_1password: no
  snap_okular: no
  snap_code: no
  snap_android_studio: no
  snap_UBports: no
  snap_insomnia: no
  snap_postman: no
  snap_dbeaver_ce: no
  snap_beekeeper_studio: no
  snap_microk8s: no
  snap_rpi_imager: no
  snap_multipass: no
  snap_zaproxy: no
  snap_cornyjokes: no
  # FLATPAK -------------------------------
  flatpak_firefox: no
  flatpak_chromium: no
  flatpak_thunderbird: no
  flatpak_flameshot: no
  flatpak_onlyoffice: no
  flatpak_1password: no
  flatpak_keepassxc: no
  flatpak_signal: no
  flatpak_telegram: no
  flatpak_threemaqt: no
  flatpak_zoom: no
  flatpak_teams: no
  flatpak_discord: no
  flatpak_spotify: no
  flatpak_ferdi: no
  flatpak_vlc: no
  flatpak_inkscape: no
  flatpak_drawio: no
  flatpak_gimp: no
  flatpak_studio: no
  flatpak_blender: no
  flatpak_code: no
  flatpak_sublimetext: no
  flatpak_arduinoide: no
  flatpak_fritzing: no
  flatpak_insomnia: no
  flatpak_postman: no
  flatpak_dbeavercommunity: no
  flatpak_filezilla: no
  flatpak_jdownloader: no
  flatpak_wireshark: no
  flatpak_ghidra: no
  flatpak_zaproxy: no
  flatpak_steam: no
  flatpak_ausweisapp2: no
  flatpak_betaflightconfigurator: no
  # OTHER --------------------------------
  vs_code_ext: no
  java: no
  steam: no
clients:
  - name: "{{ ansible_user }}"
    dev: yes
    updateOrCreate: no
```

## Dependencies

_A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles._

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: clients
  roles:
    - role: install_client
      install_client_service_name: "{{ service_name }}"
      install_client_config: []
      clients:
        - name: "{{ ansible_user }}"
          dev: yes
          updateOrCreate: no
```

## License

GNU AFFERO GENERAL PUBLIC LICENSE

## Author Information

MVladislav
