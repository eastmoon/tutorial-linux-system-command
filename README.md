# Linux systemctl and service

對於 Linux 作業系統的系統服務設計，主要有兩個方向：

+ systemctl，透過 [systemctl](https://www.freedesktop.org/software/systemd/man/systemctl.html) 管理位於 ```/lib/systemd``` 或 ```/etc/init.d``` 內的服務，可以[樣板單元檔案](https://fedoramagazine.org/systemd-template-unit-files/) 來規劃服務啟動的相關資訊
+ service，透過 service 命令管理位於 ```/etc/init.d``` 的服務，此設計依循 System V init script 的規劃，基於腳本為基礎撰寫相關命令，諸如 start、stop、restart、status 等。

對於上述兩者的用途，運用方向各有不同：

+ systemctl 是服務管理系統，運用管理多執行程序 ( Process ) 的系統
+ systemctl 執行內容涵蓋到 service 本身，因此可以替代 service 的運作範圍
+ systemctl 無法適用於 Docker 容器，因容器本身就是單一服務
+ service 適用於 Docker 容器，以此啟動安裝於容器中的額外服務，但若有多樣服務，仍建議分離於不同容器中，採用 docker-compose 啟動

## 文獻

+ 文件
    - [ubuntu - systemctl](https://manpages.ubuntu.com/manpages/bionic/zh_TW/man1/systemctl.1.html)
    - [systemctl](https://www.freedesktop.org/software/systemd/man/systemctl.html)
    - [systemd.unit — Unit configuration](https://www.freedesktop.org/software/systemd/man/systemd.unit.html)
    - [systemd.service — Service unit configuration](https://www.freedesktop.org/software/systemd/man/systemd.service.html)
    - [ubuntu - service](https://manpages.ubuntu.com/manpages/bionic/man8/service.8.html)
    - [service command](https://bash.cyberciti.biz/guide/Service_command)

+ 文獻
    - [systemctl 與 service 的分別](https://botnotes.net/2021/04/01/systemctl-service/)
    - [Linux systemd 系統服務管理基礎教學與範例](https://blog.gtwang.org/linux/linux-basic-systemctl-systemd-service-unit-tutorial-examples/)
    - [Creating templated Systemd services](https://ibug.io/blog/2019/07/systemd-service-template/)
    - [systemd: Template unit files](https://fedoramagazine.org/systemd-template-unit-files/)
    - [How can I make a script in /etc/init.d start at boot?](https://unix.stackexchange.com/questions/20357)
    - [Run a Shell Script as Systemd Service in Linux](https://www.funoracleapps.com/2022/02/run-shell-script-as-systemd-service-in.html)
        + [How do I create a service for a shell script so I can start and stop it like a daemon?](https://unix.stackexchange.com/questions/236084)
        + [How to Run a Script as a Service in Linux](https://medium.com/geekculture/how-to-run-a-script-as-a-service-in-linux-4fb92cab6818)
