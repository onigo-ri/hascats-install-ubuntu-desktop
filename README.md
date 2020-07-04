# Ubuntu Desktop�̐ݒ�

## Network�̐ݒ�

���L�̓��e��`/etc/netplan/01-network-manager-all.yaml`���쐬����

~~~
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eno1:
      dhcp4: no
      addresses: [172.21.102.22/16]
~~~

���L�̓��e��`/etc/netplan/02-network-manager-all.yaml`���쐬����

~~~
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp1s0:
      addresses: [172.22.102.22/16]
~~~

���L�̃R�}���h�����s����

~~~
$ sudo netplan apply
~~~

[Reference](https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/)

## OpenSSH Server�̐ݒ�

�C���^�[�l�b�g�ɐڑ����ĉ��L�̃R�}���h�����s����

~~~
$ sudo apt update
$ sudo apt install openssh-server
$ sudo ufw allow ssh
~~~

[Reference](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/)

## Window Manager�̐ݒ�

�f�X�N�g�b�v�����N�������ɁA����hascats-exe���N������悤�ɂ���F

���L�̓��e��`/usr/share/xsessions/custom.desktop`���쐬����

~~~
[Desktop Entry]
Name=XSession
Comment=This session uses the custom xsession file
Exec=/etc/X11/Xsession
~~~

���L�̓��e��`~/.xsession`���쐬����

~~~
#!/usr/bin/env bash

xsetroot -cursor_name left_ptr &

exec /home/mega/.local/bin/hascats-exe --workstation WS122
~~~

[XSession�̐ݒ�](https://wiki.ubuntu.com/CustomXSession)

[�}�E�X�J�[�\���̐ݒ�](https://wiki.archlinux.jp/index.php/%E3%82%AB%E3%83%BC%E3%82%BD%E3%83%AB%E3%83%86%E3%83%BC%E3%83%9E#.E5.BD.A2.E3.81.8C_X_.E3.81.AE.E3.83.87.E3.83.95.E3.82.A9.E3.83.AB.E3.83.88.E3.82.AB.E3.83.BC.E3.82.BD.E3.83.AB.E3.81.AE.E5.A4.89.E6.9B.B4)

## NTP�̐ݒ�

[https://www.yokoweb.net/2018/05/14/ubuntu-18_04-timesyncd/]

## �C���X�g�[���[�i.deb�t�@�C���j�̍쐬�ƃC���X�g�[��

`hascats.deb`�����F

�͂��߂Ƀo�C�i����`/hascats/home/mega/.local/bin/hascats-exe`��u���Be.g.,

~~~
cp /hascats/home/mega/.local/bin/hascats-exe /home/mega/hascats-install-ubuntu-desktop/hascats/home/mega/.local/bin/hascats-exe
~~~

hascats�f�B���N�g����`.deb`�Ɍł߂�B

~~~
$ cd /home/mega/hascats-install-ubuntu-desktop
$ fakeroot dpkg-deb --build hascats
~~~

��fakeroot ���Ȃ��ƌ���ꂽ�ꍇ��`sudo apt-get install fakeroot`

`hascats.deb`���C���X�g�[������F

~~~
$ sudo dpkg -i hascats.deb
~~~

[Reference](https://blog.cybozu.io/entry/2016/05/16/111500)
