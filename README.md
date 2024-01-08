[![Build Status](https://travis-ci.com/Telmate/terraform-provider-proxmox.svg?branch=master)](https://travis-ci.com/Telmate/terraform-provider-proxmox)

# Terraform provider plugin for Proxmox

This repository provides a Terraform provider for
the [Proxmox virtualization platform](https://pve.proxmox.com/pve-docs/) and exposes Terraform resources to provision
QEMU VMs and LXC Containers.

## Getting Started

In order to get started, use [the documentation included in this repository](docs/index.md). The documentation contains
a list of the options for the provider. Moreover, there are some guides available how to combine options and start
specific VMs.

## Quick Start

Follow this [install guide](docs/guides/installation.md) to install the plugin.

## Known Limitations

* `proxmox_vm_qemu`.`disk`.`size` attribute does not match what is displayed in the Proxmox UI.
* Updates to `proxmox_vm_qemu` resources almost always result as a failed task within the Proxmox UI. This appears to be
  harmless and the desired configuration changes do get applied.
* When using the `proxmox_lxc` resource, the provider will crash unless `rootfs` is defined.
* When using the Network Boot mode (PXE), a valid NIC must be defined for the VM, and the boot order must specify network first.

## Contributing

When contributing, please also add documentation to help other users.

### Debugging the provider

Debugging is available for this provider through the Terraform Plugin SDK versions 2.0.0. Therefore, the plugin can be
started with the debugging flag `--debug`.

For example (using [delve](https://github.com/go-delve/delve) as Debugger):

```bash
dlv exec --headless ./terraform-provider-my-provider -- --debug
```            - name: Setup Java JDK
  uses: actions/setup-java@v4.0.0
  with:
    # The Java version to set up. Takes a whole or semver Java version. See examples of supported syntax in README file
    java-version: # optional
    # The path to the `.java-version` file. See examples of supported syntax in README file
    java-version-file: # optional
    # Java distribution. See the list of supported distributions in README file
    distribution: 
    # The package type (jdk, jre, jdk+fx, jre+fx)
    java-package: # optional, default is jdk
    # The architecture of the package (defaults to the action runner's architecture)
    architecture: # optional
    # Path to where the compressed JDK is located
    jdkFile: # optional
    # Set this option if you want the action to check for the latest available version that satisfies the version spec
    check-latest: # optional
    # ID of the distributionManagement repository in the pom.xml file. Default is `github`
    server-id: # optional, default is github
    # Environment variable name for the username for authentication to the Apache Maven repository. Default is $GITHUB_ACTOR
    server-username: # optional, default is GITHUB_ACTOR
    # Environment variable name for password or token for authentication to the Apache Maven repository. Default is $GITHUB_TOKEN
    server-password: # optional, default is GITHUB_TOKEN
    # Path to where the settings.xml file will be written. Default is ~/.m2.
    settings-path: # optional
    # Overwrite the settings.xml file if it exists. Default is "true".
    overwrite-settings: # optional, default is true
    # GPG private key to import. Default is empty string.
    gpg-private-key: # optional
    # Environment variable name for the GPG private key passphrase. Default is $GPG_PASSPHRASE.
    gpg-passphrase: # optional
    # Name of the build platform to cache dependencies. It can be "maven", "gradle" or "sbt".
    cache: # optional
    # The path to a dependency file: pom.xml, build.gradle, build.sbt, etc. This option can be used with the `cache` option. If this option is omitted, the action searches for the dependency file in the entire repository. This option supports wildcards and a list of file names for caching multiple dependencies.
    cache-dependency-path: # optional
    # Workaround to pass job status to post job step. This variable is not intended for manual setting
    job-status: # optional, default is ${{ job.status }}
    # The token used to authenticate when fetching version manifests hosted on github.com, such as for the Microsoft Build of OpenJDK. When running this action on github.com, the default value is sufficient. When running on GHES, you can pass a personal access token for github.com if you are experiencing rate limiting.
    token: # optional, default is ${{ github.server_url == 'https://github.com' && github.token || '' }}
    # Name of Maven Toolchain ID if the default name of "${distribution}_${java-version}" is not wanted. See examples of supported syntax in Advanced Usage file
    mvn-toolchain-id: # optional
    # Name of Maven Toolchain Vendor if the default name of "${distribution}" is not wanted. See examples of supported syntax in Advanced Usage file
    mvn-toolchain-vendor: # optional
          

For more information about debugging a provider please
see: [Debugger-Based Debugging](https://www.terraform.io/docs/extend/debugging.html#debugger-based-debugging)

## Useful links

* [Proxmox](https://www.proxmox.com/en/)
* [Proxmox documentation](https://pve.proxmox.com/pve-docs/)
* [Terraform](https://www.terraform.io/)
* [Terraform documentation](https://www.terraform.io/docs/index.html)
* [Recommended ISO builder](https://github.com/Telmate/terraform-ubuntu-proxmox-iso)
