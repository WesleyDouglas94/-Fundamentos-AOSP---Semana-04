# Fundamentos-AOSP

10. Apps em Java
10.1. Executando um App no Emulador a partir do Android Studio

1. Inicie o seu emulator com o seu produto Palomakoba Zeus!.
2. Inicie o Android Studio e peça para criar um novo app no estilo Hello World. Chame esse app de HelloApp.
3. Pressione a tecla Shift+F10 no Android Studio para executar o app no emulador.
4. Observe o seu emulador executando o novo app.
![image](https://user-images.githubusercontent.com/75500077/228992406-0199c40e-e44d-43ea-b3ff-f361e7f9e146.png)

Tirar um screenshot do app rodando no seu Android.
Abra a lista dos aplicativos instalados e tire um screenshot do seu app na lista.
![image](https://user-images.githubusercontent.com/75500077/228992478-75e75f71-8c20-4e2e-906a-bdff70c63906.png)

Vá em Settings → Apps → See all 16 apps e clique no nome do seu novo app. Tirar um screenshot da tela. Note, em especial, a possibilidade de desinstalar o app.
![image](https://user-images.githubusercontent.com/75500077/228992589-45843ed2-64fe-4b7b-8a0d-4165e09cde2c.png)

Se você reiniciar o seu emulador, você irá notar que o seu novo app continua instalado. Para desinstalá-lo, use a tela de settings acima ou
(mais lento) execute o comando make installclean seguido de m. Faça isso agora, pois será necessário nas próximas seções.
![image](https://user-images.githubusercontent.com/75500077/228992875-6c59ad2f-9527-4ab3-bdef-3a37d696f1d3.png)


10.2. Incluindo o App no Produto
$ cp -r -p ~/AndroidStudioProjects/HelloApp /media/arquivos/aosp/device/palomakoba/zeus/
![image](https://user-images.githubusercontent.com/75500077/228993797-7cb12e1e-d760-476a-9786-c69c859e3ae1.png)

$ cd /media/arquivos/aosp/device/palomakoba/zeus/HelloApp
$ gedit Android.bp # Inclua nele o conteúdo abaixo
![image](https://user-images.githubusercontent.com/75500077/228994490-19e60167-27d0-422e-9579-6c37fb730203.png)

$ cd ..
$ gedit palomakoba_zeus.mk # Adicione o trecho em destaque
![image](https://user-images.githubusercontent.com/75500077/228995096-5c8c2710-d034-4e84-a6b1-521f93d190b1.png)


