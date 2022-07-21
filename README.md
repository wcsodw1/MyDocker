# MyDocker
Docker built up Tutorial and Implementation

The error when I trying to install in windows

- 1.WSL 2 installation is incomplete
    - solution1 : (就是你的Linux核心版本偏低了，該更新了。)
        - Install WSL: https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
    - Sol2 : 
        - Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All 
        - 確認Linux的Windows子系统 和 Hyper-V 有被勾選(windows功能)

- 2.Docker Desktop failed to start : 
    - a.確保下載版本為Docker 4.5 Up
    - b.將wsl2 設置為default version -> $wsl --set-default-version 2
    - c.Restart Your Computer
    and it work for me.
