# Help comandos


## Compactar e descompactar arquivos

### Arquivo .zip
    
        #Descomapctar
        unzip file.zip -d [diretorio destino]
        #Compactar
        zip -r [arquivo].zip <dir/arq>

### Arquivo .taz.gz

        #Descompactar
        taz -zxvf [arquivo].tar.gz -C /destino
        #Compactar
        tar -czvf [arquivo].tar.gz <arq1 dir1 arq2 dir2 ...>

### Arquivo .tar.bz2

        #Descompactar
        tar xjvf [arquivo].tar.bz2 -C /destino
        #Compactar
        tar -jcvf [arquivo].tar.bz2 <dir/arq>

#### Arquivo .tar

        #Compactar
        tar -cvf [novo arquivo].tar <arq1 dir1 arq2 dir2 ...>

#### Arquivo .gz

        #Compactar
        gzip [arquivo].tar

## Processos

### Listar processo ativos filtrando pelo nome

        ps aux | grepe [filtro]

### Listar processo ativos filtrando pelo porta em uso

        sudo lsof -i :[PORT]    

## Formatar PenDrive


1. Localizar onde o pendriver esta montado.

        sudo mount

2. Desmontar pendrive

        sudo umount /dev/<unidade> #ex.: sudo umount  /dev/sdb1

3. Formatar pendrive com fat32.

        mkfs.ntfs /dev/<unidade>

3.1 NTFS

        ntfslabel /dev/sdb1 <novo nome pendrive> 

#### Renomear PenDrive

1. Instalar dosfstools se não existir.
    
        sudo yum install dosfstools

2. Renomear

        sudo dosfslabel /dev/sdb1 <novo nome>

#### Montar iso

        mkdir -p /mnt/disk
        mount -o loop <arquivo>.iso /mnt/disk
 

## Instalação de Pacotes

### Listar pacotes instalados -RPM

        rpm -qa | grep <nome-pacote>
    
### Listar pacotes instalados - DEB

        dpkg -l | grep <nome-pacote>

### Instalar pacotes

        dpkg -i *.deb
        apt-get install -f #se for identificado dependencias faltantes 

## Renomear arquivos

        rename (option) 's/oldname/newname'  pattern


## Firewalls

### Iptables

        iptables -A INPUT -p <prototcol> --dport <portnumber> -j ACCEPT

### Find

find . -type d -name 'gissaBroker'

## TMUX

ctrl-b c   Create a new window
ctrl-b n   Change to next window
ctrl-b p   Change to previous window
ctrl-b &   Kill window
ctrl-b ,   name window
ctrl-b f   find window
ctrl-b "   Split pane horizontally
ctrl-b %   Split pane vertically
ctrl-b o   Move to next pane
ctrl-b x   Kill pane
ctrl-b q   Show pane numbers

[More Tmux commands](https://gist.github.com/MohamedAlaa/2961058)


## Criptografia

Encriptando dados
$ gpg -e arquivo.txt

Encriptando dados com saída ASCII 7 bits
$ gpg -e -a arquivo.txt

Encriptando dados com outra chave publica
$ gpg -r [nome/e-mail/ID] -e arquivo.txt

Decriptando dados com o gpg
$ gpg -d arquivo.txt.asc > arquivo.txt
$ gpg -d arquivo.txt.gpg > arquivo.txt

Assinando arquivos
$ gpg -s arquivo.txt

Assinando plan texts
$ gpg -s --clearsign arquivo.txt

Checando assinaturas
$ gpg --verify arquivo.txt.asc
$ gpg --verify arquivo.txt.gpg

Extraindo sua chave pública do chaveiro
$ gpg --export -a usuario >chave-pub.txt

Adicionando chaves públicas ao seu chaveiro pessoa
$ gpg --import chave-pub-usuario.txt

Listando chaves de seu chaveiro
$ gpg --list-keys

Apagando chaves de seu chaveiro
$ gpg --delete-key usuario

Mudando sua Frase Senha
$ gpg --edit-key

## LVM

  umount /home
  vgdisplay 
  pvdisplay 
  e2fsck -f /dev/mapper/mylaptop--vg-home 
  fdisk -l
  resize2fs /dev/mapper/mylaptop--vg-home 400G
  lvreduce -L -22G /dev/mapper/mylaptop--vg-home
  pvdisplay
  lvdisplay
  vgdisplay
  mount -a
  lvextend -L +16G /dev/mapper/mylaptop--vg-var
  resize2fs /dev/mapper/mylaptop--vg-var


GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_TERMINAL=console

After saving changes you need to run:

sudo update-grub
sudo systemctl enable multi-user.target --force
sudo systemctl set-default multi-user.target

Undoing text-mode

To undo sudo systemctl set-default multi-user.target simply type

sudo systemctl enable graphical.target --force
sudo systemctl set-default graphical.target 

## Image Magick

```
convert original.jpg -colorspace Gray gray.jpg
```

```
mogrify -flip *.jpg

mogrify -flop *.jpg
```

PipeWire

https://ubuntuhandbook.org/index.php/2021/05/install-latest-pipewire-ppa-ubuntu-20-04/

https://ubuntuhandbook.org/index.php/2021/05/enable-pipewire-audio-service-ubuntu-21-04/

* create an empty file /etc/pipewire/media-session.d/with-alsa

* copy /usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf
  into /etc/alsa/conf.d/
  
  cp /usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf /etc/alsa/conf.d/





