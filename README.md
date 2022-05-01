# Remote OCP Container Terminal (ROCT)

This solution uses an Ubuntu container image to build a remote environment with command line tools from several cloud vendors: IBM® Cloud, Red Hat® OpenShift®, Kubectl, Helm, etc.

The primary goal of this solution is to use Microsoft Visual Studio Code's Remote Container extension to run a remote container in an OpenShift cluster.  

The solution uses IBM File or Block (for ROKS clusters) and managed-nfs-storage (Technology Zone).

📝 For the initial setup, this solution assumes you already have `oc` client installed on your laptop (Mac/Windows/Linux).

⛔️ Choose one: Manual or Automated

## Manual Install

⤵️ See below section if you wish to automatically deploy via a bash or powershell script.

```
git clone https://github.com/aroute/roct.git
```
```
oc login ...
```
```
oc new-project roct
```
```
oc create serviceaccount roct
```
```
oc adm policy add-scc-to-user privileged -n roct -z roct
```
⛔️ Choose one: Block or File.
```
oc create -f roct-block.yaml
```
```
oc create -f roct-file.yaml
```
See below **How to attach VS Code to Remote Container**

## Automated Install

### MacOS/Linux
```
git clone https://github.com/aroute/roct.git
```
```shell
oc login ...
```
⛔️ Choose one: Block or File.

#### Block
```shell
chmod +x roct_block.sh
```
```shell
./roct_block.sh
```
#### File
```shell
chmod +x roct_file.sh
```
```shell
./roct_file.sh
```
See below **How to attach VS Code to Remote Container**

### Windows

Download this repository (zip file) and extract (see download button above). Launch PowerShell and move into the directory where you downloaded/extracted this repository.

```powershell
oc login ...
```
⛔️ Choose one: Block or File.
#### Block
```powershell
.\win_roct_block.ps1
```
#### File
```powershell
.\win_roct_file.ps1
```
See below **How to attach VS Code to Remote Container**

#### Troubleshooting PowerShell execution permission

If you receive an error message indicating that the code is not digitally signed, execute the following command:
```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

## How to attach VS Code to Remote Container

1. From VS Code running locally, install Microsoft's [Kubernetes](https://code.visualstudio.com/docs/azure/kubernetes#_install-the-kubernetes-extension) and [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extensions. 
2. Click on VS Code's Kubernetes extension icon. Drop-down the cluster with roct. Drop-down Workloads - Pods. Right-click `roct-0` pod and select Attach VS Code.
3. This opens up a new VS Code window. The extension will install some binaries on the remote container. Wait for the installation to finish and then open a folder to `/home/demo/` directory. Open a Terminal and type bash to switch to the bash prompt.
4. Log in to OpenShift `oc login ...`

**Your remote container environment with Ubuntu is all set up for you to proceed.**


