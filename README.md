# I'M NOT MAINTAINING THIS ANYMORE AS I'M NO LONGER DOING WAS.
Feel free to fork or look at one of the forks other people created.

# ansible-was

Roles for installing and managing IBM Websphere Application Server (WAS) on
*nix (tested on Debian Linux), including the IBM Installation Manager (IIM),
IBM HTTP Server (IHS) and Plugin (PLG).

## IIM

Installs the IBM Installation Manager.

### Requirements

On the OS setfacl and unzip must be installed.
- Debian: setfacl & zip
- CentOS: setfacl & unzip

The user with group {{iim_user}}:{iim_group}} must exist.

Sufficient rights for this user to create the {{iim_repo}}, {{iim_tmp}} and {{iim_path}} directories.

### Variables

- iim_user or ibm_user (iim_user: "{{ibm_user}}"): User as which to install IIM. **required**
- iim_path or ibm_root (iim_path: "{{ibm_root}}/InstallationManager"): Path where to install IIM. **required**

- ibm_repo: Location of the IBM repositories. **default**: "{{ibm_root}}/repo"
- ibm_mode: Default directory mode. **default**: "0750"
- iim_version: Minimal required version of IIM. **default**: "1.8"
- iim_path: Path where to install IIM. **default**: "{{ibm_root}}/InstallationManager"
- iim_repo: Repository containing the IIM installation files. **default**: "{{ibm_repo}}/IIM"
- iim_tmp: Temporary directory where installtion zips are temporary put before unzipping. **default**: "{{ibm_root}}/tmp"
- iim_group: Group of the iim_user. **default**: "{{iim_user}}"
- iim_mode: Mode for the directories that are created. **default**: "{{ibm_mode}}"

- iim_local_src: This will bypass all of the copying of the zip file to the
  managed node and just use a zip file on the managed node's filesystem. Use
  this if you copy the zip file yourself or mounted for instance an NFS with
  the installation zip files before.

### Example of use

See playbook-iim.yml for installing.

## WAS

Installs or uninstalls the IBM WebSphere Application Server.

### Requirements

On the OS setfacl and unzip (Debian packages acl & zip) must be installed.

The user with group {{was_user}}:{was_group}} must exist.

Sufficient rights for this user to create the {{was_repo}}, {{iim_tmp}}
and {{was_path}} directories.

### Variables

- was_user or ibm_user (was_user: "{{ibm_user}}"): User as which to install WAS
  (must also be the user IIM is installed with). **required**
- was_path  or ibm_root (was_path: "{{ibm_root}}/WebSphere". **required**
- was_repo or ibm_repo (was_repo: "{{ibm_repo}}"). **required**

- state: *installed* or *absent". **default**: installed
- was_nd: *false* or *true*. **default**: false
- ibm_repo: Location of the IBM repositories. **default**: "{{ibm_root}}/repo"
- ibm_mode: Default directory mode. **default**: "0750"
- was_version: Miniamal version required. **default**: "9.0"
- was_imcl_package_name: Name of the WAS package as required by imcl of IIM
- jdk_imcl_package_name: Name of the JDK package as required by imcl of IIM
- was_imcl_package_regex: Regex that matches the WAS package name inlcuding
  version. **default**:
  "com.ibm.websphere.BASE.v[0-9]+_([0-9]+.[0-9]+.[0-9]+.[0-9]+)"
- was_group: Group of the was_user. **default**: "{{was_user}}"
- was_mode: Mode for the directories that are created. **default**:
  "{{ibm_mode}}"

- was_local_src: This will bypass all of the copying of the WAS zip file to the
  managed node and just use a zip file on the manged node's filesystem. Use
  this if you copy the zip file yourself or mounted for instance an NFS with
  the installation zip files before.
- jdk_local_src: This will bypass all of the copying of the SDK zip file to the
  managed node and just use a zip file on the manged node's filesystem. Use
  this if you copy the zip file yourself or mounted for instance an NFS with
  the installation zip files before.

### Examples of use

See playbook-was.yml for installing.

See playbook-uninstall-was.yml for the uninstall.

## IHS (+ PLG)

Installs or uninstalls the IBM HTTP Server and Plugin.

### Requirements

On the OS setfacl and unzip (Debian packages acl & zip) must be installed.

The user with group {{ihs_user}}:{{ihs_group}} must exist.

Sufficient rights for this user to create the {{ihs_repo}}, {{plg_repo}},
{{iim_tmp}}, {{ihs_path}} and {{plg_path}} directories.

### Variables

TODO: similar to WAS but with ihs_ and plg_

### Examples of use

See playbook-ihs.yml for installing.

See playbook-uninstall-ihs.yml for the uninstall.
