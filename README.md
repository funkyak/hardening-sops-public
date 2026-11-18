# Hardening SOPs

Step-by-step hardening procedures for Windows/Active Directory, Linux, pfSense and VyOS, using built-in tools: PowerShell, Group Policy, bash and the device CLIs. Each SOP covers what to check, what to do, how to verify it and how to roll it back.

> [!WARNING]
> These commands change logins, firewalls and domain-wide settings. Read each SOP, replace the example names, and test on one non-production host first. Provided as is, with no warranty.

## Download

- **ZIP:** select **Code → Download ZIP** at the top of this page.
- **Git:**

  ```bash
  git clone https://github.com/funkyak/hardening-sops-public.git
  ```

## Read it in Obsidian (recommended)

1. In [Obsidian](https://obsidian.md), choose **Open folder as vault** and select this folder.
2. If asked, trust the vault. Then check **Settings → Appearance → CSS snippets** has **mermaid-fit** turned on, so flowcharts fit the page.
3. Start at **0 Start here**.

The notes also open on GitHub and flowcharts render there, but links between notes use Obsidian's `[[note]]` format and only work in Obsidian.

## Before you run anything

Replace these example names with your own:

| In the SOPs | Means |
|---|---|
| `gt` | The one account that keeps its password and password SSH login |
| `breakglass` | Your emergency admin account |
| `<DC>`, `<host>` | A domain controller, or the machine you are changing |
| `example.local` | Your AD domain |

## Contents

### Start

| SOP | Covers |
|---|---|
| [0 Start here](0%20Start%20here.md) | Index, names to replace, suggested order |
| [0.1 Before any change](0.1%20Before%20any%20change.md) | Backups, protected accounts, lockout recovery |

### Windows and Active Directory

| SOP | Covers |
|---|---|
| [1.1 Disable SMB1 and enforce SMB3](1%20Windows/1.1%20Disable%20SMB1%20and%20enforce%20SMB3.md) | SMB1 off, SMB3 enforced, signing, GPO |
| [1.2 Mass AD password reset with exceptions](1%20Windows/1.2%20Mass%20AD%20password%20reset%20with%20exceptions.md) | Reset all AD passwords except named accounts |
| [1.3 Move from WinRM to SSH](1%20Windows/1.3%20Move%20from%20WinRM%20to%20SSH.md) | OpenSSH from local files, keys only, GPO rollout |
| [1.4 Audit policy GPO](1%20Windows/1.4%20Audit%20policy%20GPO.md) | Advanced audit policy and logging |
| [1.5 Disable built-in Administrator](1%20Windows/1.5%20Disable%20built-in%20Administrator.md) | Disable the RID 500 account |
| [1.6 Lock down shares](1%20Windows/1.6%20Lock%20down%20shares.md) | Remove risky share permissions |
| [1.7 Block downloads in Edge](1%20Windows/1.7%20Block%20downloads%20in%20Edge.md) | Browser download restrictions |
| [1.8 Sinkhole domains in AD DNS](1%20Windows/1.8%20Sinkhole%20domains%20in%20AD%20DNS.md) | Block domains in AD DNS |

### Linux

| SOP | Covers |
|---|---|
| [2.1 SSH keys only with password exception](2%20Linux/2.1%20SSH%20keys%20only%20with%20password%20exception.md) | Keys only, with one password exception |
| [2.2 Baseline lockdown](2%20Linux/2.2%20Baseline%20lockdown.md) | sysctl, firewall, services, sudo logging |
| [2.3 Audit SSH keys](2%20Linux/2.3%20Audit%20SSH%20keys.md) | Find and remove unknown SSH keys |
| [2.4 Break-glass sudo user](2%20Linux/2.4%20Break-glass%20sudo%20user.md) | Emergency local admin |
| [2.5 Samba SMB3 only](2%20Linux/2.5%20Samba%20SMB3%20only.md) | SMB3-only Samba |

### Network devices

| SOP | Covers |
|---|---|
| [3.1 pfSense](3%20Network%20devices/3.1%20pfSense.md) | Backup, password, SSH keys, blocklists |
| [3.2 VyOS](3%20Network%20devices/3.2%20VyOS.md) | Keys, backup, restore |

### Hunting

| SOP | Covers |
|---|---|
| [4.1 Hunt for persistence](4%20Hunting/4.1%20Hunt%20for%20persistence.md) | Kibana, Velociraptor and local checks |

## License

[MIT](LICENSE)
