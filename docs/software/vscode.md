# VS Code and other IDEs

To use an IDE on Borah, please either use the 
[OnDemand VS Code app](../open_ondemand.md/#vs-code-server) 
or modify your SSH configuration settings to connect to the cluster through a 
slurm job.

Configuring the remote IDE server to work within a slurm allocation and 
connect to a compute node provides the IDE user with improved performance 
through dedicated resources and prevents user processes from slowing down the 
shared login node.

This example configures VS Code but can be extended to other IDEs or workflows.

## 1. Configure SSH access

Follow the [SSH setup](../logging_in.md/#ssh) here. If you're using Windows and
MobaXTerm, you'll also want to copy your public and private key to your user's
`.ssh` folder (usually found in `C:\Users\USERNAME\.ssh`)

## 2. Install the Remote SSH Extension in VS Code

In the "Extensions" panel in VSCode, search for and install the "Remote - SSH" 
extension.

## 3. Configure SSH

Your SSH configuration file can be found at the following location:

- MacOS / Linux: `~/.ssh/config`
- Windows: `C:\Users\USERNAME\.ssh\config`

Add the following lines to your SSH config file, replacing USERNAME with your 
username:
### MacOS / Linux:
```
Host borah
    ControlMaster auto
    ControlPath ~/.ssh/master-%r@%h:%p
    User USERNAME
    HostName borah-login.boisestate.edu

Host borah-compute
    ForwardAgent yes
    StrictHostKeyChecking no
    User USERNAME
    ProxyCommand ssh borah "salloc -J VSCode -p bsudfq -n 8 -K1 /bin/bash -c 'nc \$SLURM_NODELIST 22'"

Host borah-gpu
    ForwardAgent yes
    StrictHostKeyChecking no
    User USERNAME
    ProxyCommand ssh borah "salloc -J VSCode -p gpu-l40 --gres=gpu:1 -n 16 -K1 /bin/bash -c 'nc \$SLURM_NODELIST 22'"
```

### Windows:
```
Host borah
    User USERNAME
    HostName borah-login.boisestate.edu

Host borah-compute
    ForwardAgent yes
    StrictHostKeyChecking no
    User USERNAME
    ProxyCommand ssh borah "salloc -J VSCode -p bsudfq -n 8 -K1 /bin/bash -c 'nc $SLURM_NODELIST 22'"

Host borah-gpu
    ForwardAgent yes
    StrictHostKeyChecking no
    User USERNAME
    ProxyCommand ssh borah "salloc -J VSCode -p gpu-l40 --gres=gpu:1 -n 16 -K1 /bin/bash -c 'nc $SLURM_NODELIST 22'"
```

!!! info
    An error of "UNKNOWN" or exit code 65535 may mean that there are no 
    available nodes to allocate and the SSH connection has timed out while waiting.

## 4. Connect

In VS Code, open the remote explorer and select one of the following:

- `borah-compute`: A default Borah compute node
- `borah-gpu`: An L40 GPU node

!!! warning
    Do not connect directly to the `borah` remote host; this host points to 
    the login node and will cause contention with other users and your VS Code 
    processes will be killed by the login node service.

## How it works
The SSH configuration automates the full connection flow:

- SSH connects to the login node (`borah-login`).
- A compute node is allocated via (`salloc`).
- The connection is tunneled using (`nc`) (netcat).
- The IDE attaches directly to the compute node.


This guide is adapted from [PSC Bridges-2's recommendations for launching remote IDEs](https://www.psc.edu/resources/bridges-2/user-guide#vscode){:target="_blank"}.
