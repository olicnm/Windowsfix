https://forum.level1techs.com/t/2-gamers-1-gpu-with-hyper-v-gpu-p-gpu-partitioning-finally-made-possible-with-hyperv/172234

---------------------------------------------------------------------------------------------------------------------------------
1. When setting up HyperV. Create VMs with Gen 2. You will also need to disable enhanced sessions and Checkpoints for VMs. By Default, each HyperV VM is set to one CPU core and RAM will be set to Dynamic (if on Windows 10 and not server.). This can be changed on the VM’s Settings
2. On your host machine, go to C:\Windows\System32\DriverStore\FileRepository\
and copy the nv_dispi.inf_amd64 folder to C:\Windows\System32\HostDriverStore\FileRepository\ on your VM (This folder will not exist, so make sure to create it)
3. Next you will need to copy items from C:\Windows\System32\ from your host to C:\Windows\System32\
In your hosts System32 folder, do a search for NV*.* and copy all.
!!! PLEASE NOTE IF YOU HAVE UPDATED YOUR HOST’S VIDEO DRIVERS, YOU WILL HAVE TO RECOPY ALL DRIVERS TO YOUR VM’S OR CODE 43 WILL REAPPEAR !!!
4. You will notice that you do not have any sort of Audio Driver installed on the VM.
5. Shut VM down and configure your Powershell script for the VM. You can change out the Values as you see fit or change them to be the same as mine from the Video.
6. Run PowerShell on the host system as admin to start partitioning the GPU with Powershell with the script below.
PowerShell Script
This will be trial and error to get settings right. You can use the PowerShell command “Get-VMPartitionableGpu” to locate the total amount of resources you have available and divide it for each VM you want to assign resources to. Also if you have multiple GPUs, The name field will match the hardware ID of the card.
When Setting up the partitions, try to leave headroom on the GPU or it might throw an error stating that there aren’t any resources available. Try to leave 10% - 15% available If you seem to be getting errors when starting up a second VM (or VM#x) that would be also using the same card as another VM(s).

<code>$vm = "ENTER YOUR VM NAME HERE"
Remove-VMGpuPartitionAdapter -VMName $vm
Add-VMGpuPartitionAdapter -VMName $vm
Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionVRAM 1
Set-VMGpuPartitionAdapter -VMName $vm -MaxPartitionVRAM 11
Set-VMGpuPartitionAdapter -VMName $vm -OptimalPartitionVRAM 10
Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionEncode 1
Set-VMGpuPartitionAdapter -VMName $vm -MaxPartitionEncode 11
Set-VMGpuPartitionAdapter -VMName $vm -OptimalPartitionEncode 10
Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionDecode 1
Set-VMGpuPartitionAdapter -VMName $vm -MaxPartitionDecode 11
Set-VMGpuPartitionAdapter -VMName $vm -OptimalPartitionDecode 10
Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionCompute 1
Set-VMGpuPartitionAdapter -VMName $vm -MaxPartitionCompute 11
Set-VMGpuPartitionAdapter -VMName $vm -OptimalPartitionCompute 10
Set-VM -GuestControlledCacheTypes $true -VMName $vm
Set-VM -LowMemoryMappedIoSpace 1Gb -VMName $vm
Set-VM -HighMemoryMappedIoSpace 32GB -VMName $vm
Start-VM -Name $vm
</code>

7. Installing a Streaming Application (Rainway and Parsec)

------------------------


- Requirements -

Windows 10 Pro license (Required for HyperV)
Current GPU Drivers

- Installation Instructions -
Install HyperV (Turn Windows Features On or Off)
	- Configure virtual switch for External Network
	- Disable Enhanced Sessions

Verify GPU Compatibility
	- Check with Powershell: Get-VMPartitionableGPU

Create New VM:
	- Gen 2
	- 16GB RAM, **Uncheck Dynamic Memory**
	- 250GB HDD

VM Settings:
	- 8 CPU Cores
	- Disable Checkpoints

Start VM + Install Windows 10 Pro

- Driver Installation -

File Transfers
	- HOST - C:\Windows\System32\DriverStore\FileRepository\nv_dispi.inf_amd64_[UUID]
	- GUEST - - To C:\Windows\System32\HostDriverStore\FileRepository\nv_dispi.inf_amd64_[UUID]

	- HOST - C:\Windows\System32\nv*.* (Every file that begins with nv)
	- GUEST - C:\Windows\System32\

- GPU Partition -

Run PowerShell ISE as Administrator

Open GPU-P-Partition.ps1
	- Set $vm = [VM-NAME]
	- Set-ExecutionPolicy Unrestricted
	- Run Script with Play button

Start VM

Check to see driver is loaded

- PostInstall Steps -

Install Parsec from Parsec.app
Install VBCable Audio Device Emulator
Install USB Monitor Virtual Driver
Install Riva Tuner from: https://www.guru3d.com/files-details/rtss-rivatuner-statistics-server-download.html
    - Recommend limiting VM to 60 FPS
    - Adjust frame limits for Host and VM. Don't forget to tweak game settings.

Connect to the VM via Parsec and GAME ON!

-------------------------------------------------------

Get-VMGpuPartitionAdapter -VMName "VM Name"

And to remove them:

Get-VMGpuPartitionAdapter -VMName "VM Name" | Remove-VMGpuPartitionAdapter

--------------------------------------------------------------
