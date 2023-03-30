# Fundamentos-AOSP

9. Novos Módulos e Programas
9.1. Adicionando um Módulo Existente no Android

cd device/palomakoba/zeus/
$ gedit palomakoba_zeus.mk # Inclua no FINAL do arquivo o conteúdo abaixo

  PRODUCT_PACKAGES += \
	UniversalMediaPlayer
  
![image](https://user-images.githubusercontent.com/75500077/228693947-2e695eaf-3bef-4897-9dba-c0d368561fbd.png)

Abra o novo app e tire um screenshot.
![image](https://user-images.githubusercontent.com/75500077/228695020-0e0cb770-7bfe-4e6f-943b-8e7b58151257.png)

Copie a tag android_app do Android.bp e salve seu conteúdo.
![image](https://user-images.githubusercontent.com/75500077/228695279-c5d53204-430d-4775-9293-f2d12859984f.png)

9.2. Criando um Programa Nativo em C

$ cd device/palomakoba/zeus/
$ mkdir HelloC
$ cd HelloC
$ gedit hello_c.c #Inclua nele o conteúdo abaixo.
![image](https://user-images.githubusercontent.com/75500077/228696133-ac04cd14-06f9-422b-b49b-533b2a43b032.png)

$ gedit Android.bp # Inclua nele o conteúdo abaixo.
![image](https://user-images.githubusercontent.com/75500077/228696253-dcc922bd-e087-48f1-b9af-ac9dc03df5ac.png)

$ cd ..
$ gedit palomakoba_zeus.mk
![image](https://user-images.githubusercontent.com/75500077/228696413-1bf7a1c3-1056-45d8-8405-6341f52fef3f.png)

# ls -lh /vendor/bin/hello_c
![image](https://user-images.githubusercontent.com/75500077/228698066-2fdc1704-1ab3-4d8c-99fd-bfef631da342.png)

# hello_c
![image](https://user-images.githubusercontent.com/75500077/228698130-c25627e3-a30a-4300-9bef-2f83c818f57c.png)

# logcat -d | grep "Hello World"
![image](https://user-images.githubusercontent.com/75500077/228698250-82e7b85e-9abb-47aa-9b96-e9de929ad989.png)


9.3. Incluindo um Módulo do GitHub/LineageOS

$ cd /media/arquivos/aosp/device/palomakoba/zeus/
$ mkdir external ; cd external # Cria um diretório para os módulos externos e entra nele
$ # Clona o repositório android_external_libncurses, disponível no LineageOS (branch lineage-19.0),
$ # e coloca o conteúdo dentro do diretório libncurses (output)
$ git clone https://github.com/LineageOS/android_external_libncurses.git -b lineage-19.0 libncurses
![image](https://user-images.githubusercontent.com/75500077/228698433-ea5ec9ef-e62e-497b-8ac6-0bf0df5ad931.png)

Liste todas as variáveis declaradas no Android.mk do libncurses. Diga apenas o nome, sem repetição, na mesma ordem que foram declarados.

LOCAL_PATH
LOCAL_SRC_FILES
LOCAL_CFLAGS
LOCAL_CFLAGS
LOCAL_C_INCLUDES
LOCAL_MODULE_TAGS
LOCAL_MODULE
LOCAL_SYSTEM_EXT_MODULE
BUILD_SHARED_LIBRARY
TERMINFO_FILES
TERMINFO_SOURCE
TERMINFO_TARGET


$ git clone https://github.com/LineageOS/android_external_nano.git -b lineage-18.1 nano
![image](https://user-images.githubusercontent.com/75500077/228699366-12c8114c-b7e0-4a23-a677-2cdb56c4fb7f.png)

$ gedit nano/Android.mk
![image](https://user-images.githubusercontent.com/75500077/228699558-8947d464-628b-4a92-88c2-a675773b7c2e.png)

$ gedit /media/aosp/external/openssh/Android.bp # Inclua/Modifique o que está destacado
![image](https://user-images.githubusercontent.com/75500077/228699987-d70e5103-a63a-41fe-bf1b-d89b5e000384.png)

$ cd .. # volta para o diretório device/palomakoba/zeus/
$ gedit palomakoba_zeus.mk # Inclua o que está destacado
![image](https://user-images.githubusercontent.com/75500077/228700130-ccdd08f0-b37a-4c9e-b233-c072c8f4c134.png)


