# confluence

This role installs the Atlassian Confluence.
Configuration that is made in configuration files is automatically performed.
Further configuration is only possible through the confluence administration interface.

## Requirements

Ubuntu and an [Oracle JVM (Confluence 7 needs at least Version 8)](https://github.com/stuvusIT/oracle-java)

## Role Variables

| Name                                        | Default/Required             | Description                                                                                                                                                |
|---------------------------------------------|:----------------------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `confluence_version`                        | :heavy_check_mark:           | Version of Confluence to download and install                                                                                                              |
| `confluence_java_home`                      | `/usr/lib/jvm/java-8-oracle` | Home directory of the Java installation to use                                                                                                             |
| `confluence_java_opts`                      | `-Xms1024M -Xmx1024M`        | Options to pass to the JVM                                                                                                                                 |
| `confluence_shutdown_port`                  | `8005`                       | Shutdown port for Confluence's server.xml                                                                                                                  |
| `confluence_connector_port`                 | `8080`                       | Port to listen on for requests                                                                                                                             |
| `confluence_connector_max_threads`          | `150`                        | Maximum threads to use for the connector                                                                                                                   |
| `confluence_connector_min_spare_threads`    | `25`                         | Minimum amount of spare threads for the connector                                                                                                          |
| `confluence_connector_connection_timeout`   | `20000`                      | Timeout to wait for requests                                                                                                                               |
| `confluence_connector_max_http_header_size` | `8192`                       | Maximum header size for requests                                                                                                                           |
| `confluence_connector_accept_count`         | `100`                        | Maximum concurrent `accept` syscalls for listening                                                                                                         |
| `confluence_proxy_name`                     | ` `                          | Name of the proxy to run Confluence behind. This role assumes you use a proxy which offers confluence with TLS. Unencrypted connections are not supported. |
| `confluence_context_path`                   | ` `                          | Context path to run Confluence under.                                                                                                                      |

## Example Playbook

```yml
- hosts: confluence
  roles:
  - confluence
    confluence_version: 7.6.0
    confluence_proxy_name: wiki.example.com
    confluence_context_path: /confluence
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
