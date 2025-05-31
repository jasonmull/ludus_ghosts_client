# Ludus Ansible Role: GHOSTS Client

A Ludus-compatible Ansible role to download, install, and configure the GHOSTS client application on Windows systems.  Specifically, this role currently performs the following tasks:
 - Downloads the latest GHOSTS client zip file
 - Extracts the zip file to c:\ludus
 - Renames the extracted folder to ghosts-client to standarize between version changes
 - Sets the API URL based on the IP address of the server the ludus_ghosts_server role was installed on
 - Disables startup through the config file
 - Sets the GHOSTS executable in the HKLM run key so that it starts every startup

## Requirements

- Ludus Cyber Range
- Windows target system
- [Ludus GHOSTS Server role](https://github.com/frack113/ludus_ghosts_server/)


## Role Variables

Default values (see `defaults/main.yml`) will join to the client to the GHOSTS server provisioned within the range config file.

## Dependencies

None.

## Example Playbook

```yaml
ludus:
  - vm_name: "{{ range_id }}-WKS1"
    hostname: "{{ range_id }}ORION-WKS1"
    template: win11-23h2-x64-enterprise-template
    vlan: 250
    ip_last_octet: 21
    ram_gb: 8
    cpus: 4
    windows:
      sysprep: true
    roles:
      - jasonmull.ludus_ghosts_client
```

## License

GPLv3

## Author Information

Role created by [jasonmull](https://github.com/jasonmull), for [Ludus](https://ludus.cloud/).
