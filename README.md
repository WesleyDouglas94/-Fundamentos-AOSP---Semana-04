# -Fundamentos-AOSP---Semana-04


## 6. Sistema de Inicialização do Android ##

$ cd /media/arquivos/aosp
$ source build/envsetup,sh
$ lunch palomakoba_zeus-eng
$ emulator &
$ sleep 20 # Espera o Android iniciar
$ adb shell
![image](https://user-images.githubusercontent.com/75500077/226772632-0fe88e90-72cf-4bac-9c73-e7494a17760f.png)


6.1. Inicialização do Init

#Analise o código fonte do Kernel Linux e diga os três arquivos que o kernel verifica procurando pelo binário do Init.
![image](https://user-images.githubusercontent.com/75500077/226773680-2010d0ff-e0b1-48a2-9104-1e6fa40a314b.png)

$ cat /proc/cmdline
![image](https://user-images.githubusercontent.com/75500077/226773878-583c1ed1-5401-47d1-b623-3ef38983c888.png)

$ ls -lhfd /sbin/init /etc/init /bin/init       # f: não ordena, d: mostra nome do diretório
![image](https://user-images.githubusercontent.com/75500077/226774184-02ec4603-2cc6-4a49-9016-02f6fe0cf733.png)


6.2. Configuração do Init

$ ls /system/etc/init/
![image](https://user-images.githubusercontent.com/75500077/226774840-a8c92ff7-82f9-417d-91b5-bad0bdda3a4c.png)
getprop ro.boot.init_rc
![image](https://user-images.githubusercontent.com/75500077/226775099-6d671639-f6ba-4c6f-8f2a-d84a32f25e4d.png)
$ more /system/etc/init/hw/init.rc    # Q para sair
import /init.environ.rc
![image](https://user-images.githubusercontent.com/75500077/226776040-07a2a691-6f42-46be-be7f-d6a1324ca7a4.png)
$ import /system/etc/init/hw/init.usb.rc
![image](https://user-images.githubusercontent.com/75500077/226776111-c68309a2-7d4c-43ad-95c9-69c7ed19cb7c.png)

$ import /init.${ro.hardware}.rc
#FIM
$ import /vendor/etc/init/hw/init.${ro.hardware}.rc
#FIM
import /system/etc/init/hw/init.usb.configfs.rc
![image](https://user-images.githubusercontent.com/75500077/226776400-b85c9f8f-c919-4820-b56e-c353551cdaa1.png)
import /system/etc/init/hw/init.${ro.zygote}.rc
#FIM


6.3. Android Init Language

$ cd /system/etc/init/
$ cat surfaceflinger.rc
![image](https://user-images.githubusercontent.com/75500077/226777359-01cbb56b-669f-4824-b1e5-492aa252d3b4.png)

$ ps -eo CMD,USER,GROUP | grep surfaceflinger
![image](https://user-images.githubusercontent.com/75500077/226777560-ff74cb91-469d-4e16-b58e-751e24c8c67d.png)

$ cat bootanim.rc
![image](https://user-images.githubusercontent.com/75500077/226777620-057f129d-861b-4594-894f-2eb3c92be044.png)


6.4. Android Init Language - Actions

$ cat /init.environ.rc
![image](https://user-images.githubusercontent.com/75500077/226777868-0c12d5d5-7266-4e5e-b3ef-b7ac1d421f33.png)

$ echo $ANDROID_DATA
![image](https://user-images.githubusercontent.com/75500077/226777951-46ba4994-558e-44a6-bdc7-490b2286e72d.png)

$ dmesg | grep "processing action"
![image](https://user-images.githubusercontent.com/75500077/226778023-b5984055-d783-4397-a79a-b1ef9ea78e3a.png)

$ cat /system/etc/init/hw/init.rc | grep -A 35 "Mount filesystems and start core system services"
![image](https://user-images.githubusercontent.com/75500077/226778208-e3db4c84-a6a8-4d7e-bca2-dd58f0f64d7e.png)

$ tail -8 /system/etc/init/bootstat.rc
![image](https://user-images.githubusercontent.com/75500077/226778301-05136cb3-d5cd-44dc-9b89-024f5613f6bc.png)


# 7. Personalização do Produto - Init, Propriedades #

7.1. Cópia de Arquivos para a Imagem

$ cd /media/arquivos/aops/
$ source build/envsetup.sh
$ lunch palomakoba_zeus-eng
$ cd device/palomakoba/zeus
$ ls
![image](https://user-images.githubusercontent.com/75500077/226778682-7df64f2c-c59e-4c82-b1d8-d89b57bf1d62.png)

$ gedit palomakoba.txt           # Coloque nele o contéudo abaixo

Palomakoba Zeus! v1.0

This is my Android.
There are many like it, but this one is mine.
I must master it as I must master my life.
![image](https://user-images.githubusercontent.com/75500077/226778809-0391f10d-4d64-4e64-8ef1-4844ada1ef32.png)

$ gedit palomakoba_zeus.mk
![image](https://user-images.githubusercontent.com/75500077/226779263-28e807f5-e359-4118-bcac-edbb3e923832.png)



