## PPA (Personal Package Archive)
## 1. How does PPA work?
Ubuntu提供了[**Lunchpad**](https://launchpad.net/)平台, 讓軟體開發者可以創建自己的軟體倉庫, 使用者就可以將PPA倉庫添加進`sources.list`中, 當更新系統時, 系統也能知道是否有新軟體可以使用, 就可以以`sudo apt-get install`來安裝
#### 1.1. 使用方式
>`$sudo add-apt-repository ppa:dr-akulavich/lighttable` \
>`$sudo apt-get update`\
>`$sudo apt-get install lighttable-installer`


`sudo add-apt-repository <PPA_info>` //adds the PPA repository to the list\
`sudo apt-get update` //updates the list of the packages that can be installed on the system\
`sudo apt-get install <package_in_PPA>` //installs the package

:::warning
 
如果添加的是`ppa:dr-akulavich/lighttable`, 將會得到Light Table
如果添加的是`ppa:dr-akulavich`, 將會得到"**上層的軟體倉庫**"中所有倉庫或Packages
:::
#### 1.2. 使用說明
使用`add-apt-repository`添加PPA時, 將執行與手動運行以下這些命令相同的動作:

>`deb http://ppa.launchpad.net/dr-akulavich/lighttable/ubuntu/
YOUR_UBUNTU_VERSION_HERE main`\
>`deb-src http://ppa.launchpad.net/dr-akulavich/lighttable/ubuntu/ YOUR_UBUNTU_VERSION_HERE main`


以上兩行command是將軟體repository添加到系統中的`sources.list`文件中的方法
透過`add-apt-repository`, PPA會自動完成這些工作, 不需要考慮確切的repository URL以及OS version
:::info
使用PPA的話不會改變原本`source.list`的內容, 不過在/etc/apt/sources.list.d這個目錄中會多出兩個檔案:一個為OOO.list檔; 一個為有.save副檔名的OOO.list.save檔

帶有 .list的文件含有添加軟體倉庫的訊息的command:

![the content of .list](https://hackmd.io/_uploads/S10cM7f7T.png)

這樣可確保添加的PPA不會與`sources.list`中的文件搞混, 此外也有助於未來需移除PPA的需求
:::
## 2. 使用PPA而非使用DEB Package的好處
關於更新的流程, 如果使用DEB Package來安裝軟體的話, 不能保證在使用`sudo apt update` & `sudo apt upgrade`時, 軟體能夠被更新成較新的版本

因為`apt upgrade`主要依賴`sources.list`, 如果文件中沒有相對應的software list, 即沒有辦法透過apt標準流程做更新

#### DEB Package三種更新方法 : 
1. 有些開發者會讓使用者在安裝DEB時, 同時在`sources.list`中增加一個項目, 這樣就可以使用標準流程更新
2. 有些會在軟體運行時通知使用者有新版本可使用, 使用者需自行下載更新的Package
3. 使用者需手動查找是否有更新的版本

## 3. Remove PPA & package
#### remove the package installed by PPA
>`$sudo apt remove package_name`
#### remove PPA
>`$sudo add-apt-repository --remove ppa:PPA_name/ppa`

or
>`$ls /etc/apt/sources.list.d` //尋找需要刪除的PPA list\
>`$sudo rm -i /etc/apt/sources.list.d/PPA_name.list` //刪除PPA\

:::info
`PPA_name`的部分要改成欲刪除之正確的PPA name
:::


