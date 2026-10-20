# Install Terraform on Debian Linux

This guide explains how to install the Terraform CLI on Debian Linux using HashiCorp's official APT repository.

**Installation method:** APT package manager  
**Prerequisites:** Debian Linux, internet access, and a user account with `sudo` privileges  
**Cloud subscription:** Not required

## 1. Check Your System

Open a terminal and identify your Debian version and CPU architecture.

```bash
cat /etc/os-release
dpkg --print-architecture
```

These commands display your operating system details and package architecture.

Common architecture values:

- `amd64` — 64-bit x86 processors
- `arm64` — 64-bit ARM processors

Check whether Terraform is already installed:

```bash
terraform version
```

If the command is not found, continue with the installation steps.

## 2. Update APT and Install Prerequisites

```bash
sudo apt update
sudo apt install -y gpg wget ca-certificates
```

**What these commands do:**

- `apt update` refreshes package indexes.
- `gpg` supports verification of package-signing keys.
- `wget` downloads files from the internet.
- `ca-certificates` provides trusted certificate authorities for secure connections.

## 3. Add HashiCorp's GPG Signing Key

Download and install the official HashiCorp repository signing key into a dedicated keyring.

```bash
wget -O- https://apt.releases.hashicorp.com/gpg \
  | sudo gpg --dearmor \
  -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

Verify that the keyring file exists:

```bash
ls -l /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

### Verify the key fingerprint

```bash
gpg --no-default-keyring \
  --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
  --fingerprint
```

Compare the displayed fingerprint with HashiCorp's currently published fingerprint at:

https://www.hashicorp.com/security

**Security note:** Do not skip fingerprint verification when documenting a security-conscious installation procedure. The expected fingerprint can change when HashiCorp rotates its signing key.

## 4. Add the Official HashiCorp APT Repository

First, identify your Debian release codename:

```bash
. /etc/os-release
echo "$VERSION_CODENAME"
```

For example, a Debian installation might report `trixie` or `bookworm`.

Check the supported distributions in HashiCorp's official packaging guide before proceeding:

https://www.hashicorp.com/en/official-packaging-guide

Add the repository using your system's architecture and codename:

```bash
. /etc/os-release

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com ${VERSION_CODENAME} main" \
  | sudo tee /etc/apt/sources.list.d/hashicorp.list
```

This creates `/etc/apt/sources.list.d/hashicorp.list` with the official repository configuration.

Verify its contents:

```bash
cat /etc/apt/sources.list.d/hashicorp.list
```

The output should contain the HashiCorp APT repository URL and your Debian codename.

## 5. Refresh Package Indexes

```bash
sudo apt update
```

APT will now retrieve package metadata from the configured repositories.

Check whether Terraform is available:

```bash
apt-cache policy terraform
```

Look for a candidate version. If no candidate is available, check the Debian codename, architecture, repository configuration, and APT error messages.

## 6. Install Terraform

```bash
sudo apt install -y terraform
```

APT downloads and installs the Terraform package and makes the executable available through the system's command search path.

## 7. Verify the Installation

Check the installed version:

```bash
terraform version
```

Check which executable is being used:

```bash
command -v terraform
```

Check the installed package details:

```bash
dpkg -s terraform
```

**Expected result:** Terraform prints its installed version, and the executable can be located without specifying its full path.

Record the actual version installed in your lab notes rather than hardcoding an assumed version into this guide.

## 8. Verify Basic CLI Functionality

Check the available commands:

```bash
terraform -help
```

You should see Terraform's help output and commonly used commands such as `init`, `plan`, `apply`, and `destroy`.

No cloud credentials or subscription are required to run these CLI checks.

## 9. Common Troubleshooting

| Problem | What to check |
| --- | --- |
| `terraform: command not found` | Verify package installation using `dpkg -s terraform` and check `command -v terraform`. |
| `Unable to locate package terraform` | Run `sudo apt update` and inspect `apt-cache policy terraform`. |
| Repository returns an error | Verify your Debian codename and whether HashiCorp supports that release. |
| GPG or signature errors | Recheck the official key, fingerprint, keyring path, and repository configuration. |
| Network or TLS errors | Check internet connectivity, system time, and certificate configuration. |

Avoid bypassing repository signature checks to work around installation errors.

## 10. Uninstall Terraform

If you need to remove Terraform later:

```bash
sudo apt remove terraform
```

This removes the installed package but leaves the HashiCorp repository configuration and signing key in place.

To remove those as well, if they are no longer needed:

```bash
sudo rm /etc/apt/sources.list.d/hashicorp.list
sudo rm /usr/share/keyrings/hashicorp-archive-keyring.gpg
sudo apt update
```

Only remove these files if you no longer need the HashiCorp APT repository or its signing key for other HashiCorp packages.

## Official References

- [Terraform Installation Guide](https://developer.hashicorp.com/terraform/install)
- [HashiCorp Official Packaging Guide](https://www.hashicorp.com/en/official-packaging-guide)
- [HashiCorp Security](https://www.hashicorp.com/security)

## Verification Checklist

- [ ] Identified the Debian release and architecture.
- [ ] Installed the required prerequisites.
- [ ] Added and verified HashiCorp's signing key.
- [ ] Configured the official APT repository.
- [ ] Installed Terraform using APT.
- [ ] Verified the installed version and executable.
- [ ] Documented any errors and their solutions.

**Status:** Update this checklist only after completing and verifying the corresponding steps on a Debian system.
