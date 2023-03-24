# 8. Personalização do Produto - Overlay,Boot Animation #

8.1. Overlay - Modificando Arquivos XML

$ cd /media/arquivos/aosp/device/palomakoba/zeus/
$ mkdir overlay
$ gedit palomakoba_zeus.mk # No FINAL do arquivo, inclua o código abaixo
# Seta o diretório de overlays
PRODUCT_PACKAGE_OVERLAYS = device/palomakoba/zeus/overlay
![image](https://user-images.githubusercontent.com/75500077/227389730-7cfb9ffd-e1a4-44c3-a365-56632cc8186f.png)


alve o comentário que descreve a configuração de nome config_supportAutoRotation. Note, em especial, a parte que diz que todas as opções de rotação são removidas das configurações (settings).
![image](https://user-images.githubusercontent.com/75500077/227390343-76a64ffd-139f-4e4e-b338-027b25aec086.png)

Quando o emulador carregar, abra as configurações do Android (app Settings) e vá na opção Display. Vá para o final da lista e note que existe a opção "Auto-rotate screen". Tire um screenshot do Android mostrando a opção Auto-rotatescreen da tela de Settings do Display.
![image](https://user-images.githubusercontent.com/75500077/227390658-b644f56b-ef37-4526-b9a1-fad0c536d646.png)


 cd /media/arquivos/aosp/
$ mkdir -p overlay/frameworks/base/core/res/res/values/
$ gedit overlay/frameworks/base/core/res/res/values/config.xml

<resources>
<!-- Remove a rotação automática do dispositivo -->
<bool name="config_supportAutoRotation">false</bool>
</resources>
![image](https://user-images.githubusercontent.com/75500077/227391393-b8cc5a49-4281-4097-a7a3-e54fcb6b1762.png)

Feche o emulator aberto e, em seguida, compile o AOSP e inicie o emulator novamente:
$ m
$ emulator
![image](https://user-images.githubusercontent.com/75500077/227393469-64da633a-4c26-4124-8e64-c477b6dcb169.png)

Observando o arquivo original config.xml, copie e salve o comentário que descreve a configuração de nome config_longPressOnPowerBehavior.
![image](https://user-images.githubusercontent.com/75500077/227393724-87b66c90-e765-458a-937b-b5e53a58bf51.png)

Feche o emulador, compile o código, inicie o emulador novamente e aperte o botão de power por uns dois segundos para observar que agora aparece uma caixa de diálogo perguntando se você deseja realmente desligar o dispositivo. 
![image](https://user-images.githubusercontent.com/75500077/227396193-40adfdf4-33a5-4e07-aa20-57526dbb8dda.png)

Acesse o arquivo original config.xml, copie e salve o comentário que descreve a configuração de nome config_dialogCornerRadius.
![image](https://user-images.githubusercontent.com/75500077/227396294-a58478b9-0b5a-4f6c-927a-8e26c2ccc41a.png)

Feche o emulador, compile o código, inicie o emulador novamente e aperte o botão de power por uns dois segundos para observar que agora aparece uma caixa de diálogo perguntando se você deseja realmente desligar o dispositivo. 
![image](https://user-images.githubusercontent.com/75500077/227396954-9e6305fa-53b6-4a6f-b122-81ee228d6e5d.png)

8.2 Overlay - Modificando o App Settings

    <string name="build_number">Build number</string>
    
$ cd device/palomakoba/zeus/
$ mkdir -p overlay/packages/apps/Settings/res/values/ #Mesmo path/caminho do arquivo original
![image](https://user-images.githubusercontent.com/75500077/227397715-0755062c-06a0-47ed-9f26-756fe89398f3.png)

$ cd device/palomakoba/zeus/
$ mkdir -p overlay/packages/apps/Settings/res/values/ #Mesmo path/caminho do arquivo original

<resources>
<string name="build_number">Build number (Zeus!)</string>
</resources>
![image](https://user-images.githubusercontent.com/75500077/227399618-5118c6ab-2c4b-4b2e-bed6-82fdb77d037a.png)

8.3 Overlay - Modificando o Wallpaper Padrão

$ mkdir -p overlay/frameworks/base/core/res/res/drawable-nodpi/
$ cp ~/Downloads/default_wallpaper.png overlay/frameworks/base/core/res/res/drawable-nodpi/
Feche o emulador, compile o AOSP, inicie o emulador novamente. Note o novo wallpaper. Tire um screenshot do Android mostrando o novo wallpaper.
![image](https://user-images.githubusercontent.com/75500077/227402910-12d8662b-0ab0-4663-a25c-c6634e0773d6.png)






