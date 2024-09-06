# linux-in-practice-2nd

「Linuxのしくみ 増補改訂版」の実験コードです

# 実験プログラム実行環境の作成

お手元のUbuntu 20.04環境で本書の実験プログラムを実行する際は、以下のコマンドを実行して必要パッケージのインストールおよびユーザ設定をしてください。

```console
$ sudo apt update && sudo apt install binutils build-essential golang sysstat python3-matplotlib python3-pil fonts-takao fio qemu-kvm virt-manager libvirt-clients virtinst jq docker.io containerd libvirt-daemon-system
$ sudo adduser `id -un` libvirt
$ sudo adduser `id -un` libvirt-qemu
$ sudo adduser `id -un` kvm
```


## 環境設定

```bash
multipass list

multipass launch --cpus 2 --disk 40G --memory 8G --name my-linux-practice lts
multipass mount . my-linux-practice:/mnt/share

multipass info my-linux-practice

# enter 
multipass shell my-linux-practice
```

## set up 

```bash
sudo apt-get update
sudo apt install golang-go -y

sudo apt-get install sysstat -y
sudo vi /etc/default/sysstat
# ENABLED="false"
#  ↓
# ENABLED="true"
sudo /etc/init.d/sysstat start
```

### 起動

```bash
multipass start my-linux-practice
```

### 再起動

```bash
multipass restart my-linux-practice
```

### 停止

```bash
multipass stop my-linux-practice
```

### 削除

```bash 
multipass delete my-linux-practice
```