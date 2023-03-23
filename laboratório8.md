# 8. Personalização do Produto - Overlay,Boot Animation #

8.1. Overlay - Modificando Arquivos XML

$ cd /media/arquivos/aosp/device/palomakoba/zeus/
$ mkdir overlay
$ gedit palomakoba_zeus.mk # No FINAL do arquivo, inclua o código abaixo
# Seta o diretório de overlays
PRODUCT_PACKAGE_OVERLAYS = device/palomakoba/zeus/overlay

