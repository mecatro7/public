# Azure에서 CLI를 사용하여 Virtual Machine (VM)을 생성하는 방법
## Azure Compute Gallery에서 일반화된 이미지를 사용하여 VM을 생성하는 방법:
- 이미지 정의를 확인하고 이미지 ID를 얻으려면 다음 명령을 사용하세요:

    az sig image-definition list --resource-group <리소스 그룹 이름> --gallery-name <갤러리 이름> --query "[].[name, id]" --output tsv

- 최신 이미지 버전을 사용하려면 --image를 이미지 정의의 ID로 설정하세요. 예를 들어, Linux VM을 생성하는 경우 다음과 같이 사용합니다:

    az vm create --resource-group <VM 리소스 그룹 이름> --name <VM 이름> --image <이미지 정의 ID> --admin-username <사용자 이름> --generate-ssh-keys

- 특정 버전을 사용하려면 --image 매개변수에 이미지 버전 ID를 지정하세요. 예를 들어, 이미지 버전 1.0.0을 사용하려면 다음과 같이 입력합니다:

    az vm create --resource-group <VM 리소스 그룹 이름> --name <VM 이름> --image "/subscriptions/<subscription ID where the gallery is located>/resourceGroups/myGalleryRG/providers/Microsoft.Compute/galleries/myGallery/images/myImageDefinition/versions/1.0.0" --admin-username <사용자 이름> --generate-ssh-keys

- 기존 VHD 이미지를 사용하여 VM을 생성하는 방법:


## 기존 VHD 이미지를 사용하여 VM을 생성하려면 다음 명령을 사용하세요:
    
    az vm create -n MyVm -g <리소스 그룹 이름> --use-unmanaged-disk --os-type linux --public-ip-address "" --attach-os-disk <VHD 이미지 URL>

- 예를 들어, 기존 VHD 이미지를 사용하여 Linux VM을 생성하려면 다음과 같이 입력합니다:

    az vm create -n MyVm -g <리소스 그룹 이름> --use-unmanaged-disk --os-type linux --public-ip-address "" --attach-os-disk https://jasonvm2disks653.blob.core.windows.net/vhds/jasonvm220170915094051.vhd

이 명령은 SSH로 보안된 Linux VM을 생성합니다. Windows VM을 생성하거나 Linux VM을 비밀번호로 보안하려면 --generate-ssh-keys를 제거하여 비밀번호를 입력하도록 하세요.
