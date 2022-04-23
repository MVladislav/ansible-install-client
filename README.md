# Role Name

_A brief description of the role goes here._

## Requirements

_Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required._

## Role Variables

```yml
install_client_service_name: default-client
install_client_config:
  # GENERAL -------------------------------
  dev: false
  fonts: false
  # GNOME ---------------------------------
  gnome_gui_setup: false # general of gnome setup should be triggered, below specific what (dependencies will than general installed)
  gnome_gui_setup_theme: false
  gnome_gui_setup_dependencies: false
  gnome_gui_setup_extensions: false
  gnome_gui_setup_keybinding: false
  gnome_gui_setup_overlay: false
  # APT -----------------------------------
  apt_base: false
  apt_base2: false
  apt_snap: false
  apt_flatpak: false
  apt_peek: false
  apt_wireshark: false
  apt_wireshark_dev: false
  apt_vpn: false
  apt_gnome_boxes: false
  apt_latex: false
  apt_pandoc: false
  apt_virt_viewer: false
  # DPKG ----------------------------------
  # dpkg_virtualbox: false
  dpkg_mongodb: false
  dpkg_veracrypt: false
  # DIST KEY ------------------------------
  distribution_key_virtualbox: false
  # SNAP ----------------------------------
  snap_chromium: false
  snap_thunderbird: false
  snap_libreoffice: false
  snap_onlyoffice_desktopeditors: false
  snap_signal_desktop: false
  snap_telegram_desktop: false
  snap_zoom_client: false
  snap_spotify: false
  snap_inkscape: false
  snap_drawio: false
  snap_gimp: false
  snap_darktable: false
  snap_vlc: false
  snap_obs_studio: false
  snap_flameshot: false
  snap_1password: false
  snap_okular: false
  snap_code: false
  snap_android_studio: false
  snap_UBports: false
  snap_insomnia: false
  snap_postman: false
  snap_dbeaver_ce: false
  snap_beekeeper_studio: false
  snap_microk8s: false
  snap_rpi_imager: false
  snap_multipass: false
  snap_zaproxy: false
  snap_cornyjokes: false
  # FLATPAK -------------------------------
  flatpak_firefox: false
  flatpak_chromium: false
  flatpak_thunderbird: false
  flatpak_extension_manager: false
  flatpak_flameshot: false
  flatpak_onlyoffice: false
  flatpak_1password: false
  flatpak_keepassxc: false
  flatpak_signal: false
  flatpak_telegram: false
  flatpak_threemaqt: false
  flatpak_zoom: false
  flatpak_teams: false
  flatpak_discord: false
  flatpak_spotify: false
  flatpak_ferdi: false
  flatpak_vlc: false
  flatpak_inkscape: false
  flatpak_drawio: false
  flatpak_gimp: false
  flatpak_studio: false
  flatpak_blender: false
  flatpak_code: false
  flatpak_sublimetext: false
  flatpak_arduinoide: false
  flatpak_fritzing: false
  flatpak_insomnia: false
  flatpak_postman: false
  flatpak_dbeavercommunity: false
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
  java: false
clients:
  - name: "{{ ansible_user }}"
    dev: yes
    updateOrCreate: false
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
          updateOrCreate: false
```

## License

GNU AFFERO GENERAL PUBLIC LICENSE

## Author Information

MVladislav
