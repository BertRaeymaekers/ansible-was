# ansible-was

Roles for installing and managing IBM Websphere Application Server (WAS),
including the IBM Installation Manager (IIM), IBM HTTP Server (IHS)  and
Plugin (PLG).

## IIM

Installs the IBM Installation Manager

### Requirements

On the OS setfacl and unzip (packages acl & zip).
The user/group {{iim_user}} and {{iim_group}} must exist.
Sufficient rights for this user to create the {{iim_repo}}, {{iim_tmp}} and {{iim_path}}.

### Variables

- iim_user or ibm_user (iim_user: "{{ibm_user}}"): User as which to install IIM *required*
- iim_path or ibm_root (iim_path: "{{ibm_root}}/InstallationManager"): Path where to install IIM *required*
- ibm_repo: Location of the IBM repositories. *default*: "{{ibm_root}}/repo"
- ibm_mode: Default directory mode. *default*: "0750"
- iim_version: Minimal required version of IIM. *default*: "1.8"
- iim_path: Path where to install IIM. *default*: "{{ibm_root}}/InstallationManager"
- iim_repo: Repository containing the IIM installation files. *default*: "{{ibm_repo}}/IIM"
- iim_tmp: Temporary directory where installtion zips are temporary put before unzipping. *default*: "{{ibm_root}}/tmp"
- iim_group: Group of the iim_user. *default*: "{{iim_user}}"
- iim_mode: Mode for the directories that are created. *default*: "{{ibm_mode}}"

### Example of use

See playbook-iim.yml
