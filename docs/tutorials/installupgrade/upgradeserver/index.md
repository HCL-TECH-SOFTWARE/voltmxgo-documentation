# Upgrade Volt MX Go server components

The topic guides you in upgrading the following server components of Volt MX Go.

- Volt Foundry
- Domino REST API

## Volt MX Go v10.0

The upgrade process for Volt Foundry in Volt MX Go v10 differs from other releases. In Volt MX Go v10, the supported version of Volt Foundry is installed and then activated with a Volt MX Go license in My HCLSoftware Portal for the Volt MX Go features to work.

Using this installation option would require you to use your own Domino server.

Before starting the installation, ensure you meet the [System requirements](../sysreq/index.md).  

[Proceed to the upgrade instructions.](upgradev10.md)

??? note "Volt MX Go v2.1 up to 2.1.2"

    ## Volt MX Go v2.1 up to 2.1.2

    !!! warning "Important"

        - The upgrade processes for Volt Foundry in the Volt MX Go v2.1 up to v2.1.2 differ from other releases:
        
            - Volt Foundry is first installed, followed by installing the necessary plugins using the Volt MX Go Plugin Installer. The plugins enable the capabilities unique to Volt MX Go. Additionally, the plugins must be reinstalled each time Volt Foundry is upgraded.

            - Volt Foundry must be licensed with a Volt MX Go entitlement for the plugins to be enabled and for the Volt MX Go features to work.
        
        - Using this installation option would require you to use your own Domino server.
        
        - Before starting the installation, make sure to verify that you meet the [System requirements](../sysreq/index.md).

    - [Proceed to the upgrade instructions](versupgradedrapi.md)


??? note "Volt MX Go v2.0.4 or earlier - EOS"

    ## Volt MX Go v2.0.4 or earlier - EOS

    --8<-- "endofsupport.md"

    [Proceed to the upgrade instructions](versionupgrade.md)


