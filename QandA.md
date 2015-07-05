#系統Q&A
------

##Q1：為什麼我的虛擬機器沒有辦法順利的開機？

根據不同的情況，分成兩種解決方式：


* 你的電腦的虛擬化技術功能沒有開啟。解法：進入BIOS，將『Virtualization Technology』enabled。（ 參考網址：http://www.sysprobs.com/disable-enable-virtualization-technology-bios ）
* 如果無法從BIOS中無法開啟，通常代表您的電腦並不支援虛擬化技術。建議之後攜帶較新的電腦過來。
*  或許可以嘗試降級您的Virtualbox（ http://ubuntuforums.org/showthread.php?t=2236348 ）

##Q2：共用資料夾是做什麼用的？

在這幾天的課程中，虛擬機器（Ubuntu workstation）只是程式執行的環境。實際上我們在練習程式碼時，仍然是在您自己的電腦（Windows or Mac）編輯。

透過共用資料夾，我們可以讓虛擬機器（Ubuntu workstation）讀到我們在自己的電腦（本地端）寫好的程式。

##Q3：所以，要怎麼設定我的共用資料夾？


請參考講義第30～32頁。設定主要分為兩個步驟：

* 在外部（Windows或Mac的Virtualbox中）：設定本機路徑，作為共用資料夾位置。（講義30～32頁）
* 在內部（虛擬機器中）找到已經掛載好的共用資料夾：

    ```
    cd /media/
    ls # <-列出目錄底下的資料夾
    ```

『sf_{您設定的資料夾的名稱}』資料夾就是您的共用資料夾。你可以在本地端新增一個檔案，並觀察兩邊是否同步。範例： 
    
```
    ubuntu-workstation ~ $ cd /media
    ubuntu-workstation /media $ ls
    cdrom  sf_data  sf_nispc
    ubuntu-workstation /media $ cd sf_nispc/
    ubuntu-workstation /media/sf_nispc $ ls
    Movies          Desktop               
    Music           Documents            
    Pictures        Downloads              
    Public          Library             
    VirtualBox VMs
    ubuntu-workstation /media/sf_nispc $
    ```

##Q4：ssh為什麼無法連線？

請在 cygwin （Mac 請直接開啟 Terminal.app 即可，無須安裝 cygwin）底下執行 ssh 指令，不是在 VirtualBox 底下執行，VirtualBox 裡面的 Linux 通常會是鎖在機房裡面的伺服器，所以要用我們的 cygwin

