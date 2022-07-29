# MyDocker
Docker built up Tutorial and Implementation

## 1.The error when I trying to install in windows

- A.WSL 2 installation is incomplete
    - solution1 : (就是你的Linux核心版本偏低了，該更新了。)
        - Install WSL: https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
    - Sol2 : 
        - Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All 
        - 確認Linux的Windows子系统 和 Hyper-V 有被勾選(windows功能)

- B.Docker Desktop failed to start : 
    - a.確保下載版本為Docker 4.5 Up
    - b.將wsl2 設置為default version -> $wsl --set-default-version 2
    - c.Restart Your Computer
    and it work for me.

## 2.Concept : 
    - Image are read-only : If you wanna change something, you need to rebuilt the image($docker build .)  
    - Layers Base : Every command in the Dockerfile represent a layer
        - 實際的使用案例如檔案B_Image_Layer 當中Dockerfile針對layer進行優化(將COPY package.json提到npm install 前, 後續再COPY所有,  因此當重新docker build . 中 npm 掃到json檔發現內容無更動時, 就會省略duplicate, 因此整個運算效率就會大幅加快)

## 3.Command that I used during the process:
    - Docker Build image : 
        - $docker build . #(!) rebuild image use the same command
    - Docker run image 
        - $docker run "image" (ex : docker run -p 3000:80 f09618ed686df3c73062a71b5e3ce1c0226f0f6f0c4a580354cda4f4df5a3701)
        - shortcut : and actually we can briefly use image like : (docker run -p 3000:80 f09 or docker run -p 3000:80 f) # -p mean "publish"

    - Check current container ID/ current 主機映射到container的狀態 Image container : 
        - $docker ps or $docker container ls
        - $docker ps -a 

    - Stop container : 
        - $ docker stop "container name(ID)"(ex : docker stop 4b223e7cc8c5)
    - Remove Container : 
        - $ docker remove "container name(ID)"(ex : docker rm 4b223e7cc8c5)

    - Remove not use container(移除所有未使用的 Docker 項目) : 
        - $docker system prune