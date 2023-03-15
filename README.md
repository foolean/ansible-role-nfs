# ansible-role-nfs

Ansible role to manage nfs


## Requirements

    None


## Dependencies

    None


## Role Variables


### Server

    * nfs_server_enable

    Specify whether or not NFS server should be installed (true) or removed
    (false)

    (default: false)

    * nfs_server_exports

    Dictionary of NFS exports to be added.  The dictionary should follow the
    options listed below.  "client" can be hostname, fqdn, ip, or cidr block

    Example:
    nfs_server_exports:
      /path/to/export:
        client: "<export_options>"


### Client

    * nfs_client_enable

    Specify whether or not NFS client should be installed (true) or removed
    (false)

    (default: false)

    * nfs_client_mounts

    Dictionary of NFS mounts to be added. The dictionary should follow the
    options in the ansible.posix.mount module.  The src and path options are
    required.

    Example:
    nfs_client_mounts:
      - src: "nfs.server.org:/path/to/export"
        path: "/local/mountpoint"
      - src: "other.nfs.server.org:/path/to/export"
        path: "/local/other/mountpoint"
        opts: "rsize=262144,wsize=262144"

    (default: null)


## Example playbook

    ```yaml
    ---
    - hosts: all

      roles:
          - foolean/nfs
    ```


## Supported operating systems

    * Debian (11)
    * Raspbian (11)
    * RedHat (8)
    * Rocky (8)


## Compliance

    * CIS Debian Linux 11 Benchmark v1.0.0
    * CIS RedHat Enterprise Linux 8 Benchmark v2.0.0
    * CIS Rocky Linux 8 Benchmark v1.0.0


## License

    BSD-3-Clause
