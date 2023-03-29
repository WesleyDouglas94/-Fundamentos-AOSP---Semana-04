# Fundamentos-AOSP

5. Criando um Novo Produto


5.1. Convenções de Nomes e Diterórios

$ cd /media/arquivos/aosp
$ ls device

![image](https://user-images.githubusercontent.com/75500077/225477749-ae5ab2d5-c7ef-49fc-be1c-252cf762fb85.png)


ls device/google

![image](https://user-images.githubusercontent.com/75500077/225477940-0b60f8cd-728f-4611-b5a6-2f0644f0915a.png)

$ gedit build/target/board/emulator_x86_64/BoardConfig.mk
![image](https://user-images.githubusercontent.com/75500077/225478607-915e5969-961c-4a37-a9d0-d8d1732dd64e.png)


5.3. Criando e Compilando um Novo Produto

$ mkdir -p device/palomakoba/zeus/
$ cd device/palomakoba/zeus/
$ gedit AndroidProducts.mk
![image](https://user-images.githubusercontent.com/75500077/225479303-a6621d06-b7af-4a1d-a659-c5da6fad4521.png)


$ gedit palomakoba_zeus.mk 
![image](https://user-images.githubusercontent.com/75500077/225479606-5ea3b97a-64f5-4597-bd1b-2c0e2696d05c.png)

$ gedit BoardConfig.mk
![image](https://user-images.githubusercontent.com/75500077/225479728-2992265c-350f-4c27-824b-6180b08049ea.png)

$ source build/envsetup.sh
$ lunch 
![image](https://user-images.githubusercontent.com/75500077/225479992-e76689d3-19cd-4032-995e-8946c5fc078b.png)

$ lunch palomakoba_zeus-eng
![image](https://user-images.githubusercontent.com/75500077/225480151-595c7573-2baf-40ab-b9bd-99a1eff5cef6.png)

$ source build/envsetup.sh  # configura o terminal
$ lunch # Seleciona o número do seu produto ou pressione CTRL+C e execute o próximo comando
$ lunch palomakoba_zeus-eng
$ m- j8

![image](https://user-images.githubusercontent.com/75500077/225772523-39a96bbb-4abb-412c-b377-cdc221f4918c.png)
 
 
 5.4. Executando o Novo Produto Criado
 
$ emulator
![image](https://user-images.githubusercontent.com/75500077/225774476-c841706d-a452-407f-a4f4-fc8d7cf55455.png)


5.5. Investigando as Configurações do Emulador

$ gedit build/target/product/sdk_phone_x86_64.mk


```

# All components inherited here go to system image

$(call inherit-product, $(SRC_TARGET_DIR)/product/core_64_bit.mk)
#FIM

$(call inherit-product, $(SRC_TARGET_DIR)/product/generic_system.mk)
#INICIO
 $(call inherit-product, $(SRC_TARGET_DIR)/product/handheld_system.mk)
   $(call inherit-product, $(SRC_TARGET_DIR)/product/media_system.mk)
   $(call inherit-product-if-exists, frameworks/base/data/fonts/fonts.mk)
   $(call inherit-product-if-exists, external/google-fonts/dancing-script/fonts.mk)
   $(call inherit-product-if-exists, external/google-fonts/carrois-gothic-sc/fonts.mk)
   $(call inherit-product-if-exists, external/google-fonts/coming-soon/fonts.mk)
   $(call inherit-product-if-exists, external/google-fonts/cutive-mono/fonts.mk)
   $(call inherit-product-if-exists, external/google-fonts/source-sans-pro/fonts.mk)
   $(call inherit-product-if-exists, external/noto-fonts/fonts.mk) 
   $(call inherit-product-if-exists, external/roboto-fonts/fonts.mk)
   $(call inherit-product-if-exists, external/hyphenation-patterns/patterns.mk)
   $(call inherit-product-if-exists, frameworks/base/data/keyboards/keyboards.mk)
   $(call inherit-product-if-exists, frameworks/webview/chromium/chromium.mk)
#FIM
 
 
 
 $(call inherit-product, $(SRC_TARGET_DIR)/product/telephony_system.mk)
#FIM
 
 $(call inherit-product, $(SRC_TARGET_DIR)/product/languages_default.mk)
#FIM
 
 $(call inherit-product-if-exists, vendor/google/security/adb/vendor_key.mk)
NÂO EXISTE
#FIM

 $(call inherit-product, $(SRC_TARGET_DIR)/product/updatable_apex.mk)
#FIM


# All components inherited here go to system_ext image
$(call inherit-product, $(SRC_TARGET_DIR)/product/handheld_system_ext.mk)
  #INICIO
   $(call inherit-product, $(SRC_TARGET_DIR)/product/media_system_ext.mk)
     $(call inherit-product, $(SRC_TARGET_DIR)/product/base_system_ext.mk)
  #FIM
  
$(call inherit-product, $(SRC_TARGET_DIR)/product/telephony_system_ext.mk)
 #FIM
 
 
# All components inherited here go to product image
$(call inherit-product, $(SRC_TARGET_DIR)/product/aosp_product.mk)
#INICIO
  $(call inherit-product, $(SRC_TARGET_DIR)/product/handheld_product.mk)
    $(call inherit-product, $(SRC_TARGET_DIR)/product/media_product.mk)
      $(call inherit-product, $(SRC_TARGET_DIR)/product/base_product.mk)
      
  $(call inherit-product, $(SRC_TARGET_DIR)/product/telephony_product.mk) 
  FIM
  
  $(call inherit-product-if-exists, frameworks/base/data/sounds/AllAudio.mk)
  FIM
#FIM

# All components inherited here go to vendor image
$(call inherit-product-if-exists, device/generic/goldfish/x86_64-vendor.mk)
#FIM

$(call inherit-product, $(SRC_TARGET_DIR)/product/emulator_vendor.mk)
 #INICIO
  $(call inherit-product, $(SRC_TARGET_DIR)/product/handheld_vendor.mk)
    $(call inherit-product, $(SRC_TARGET_DIR)/product/media_vendor.mk)
     $(call inherit-product, $(SRC_TARGET_DIR)/product/base_vendor.mk)
     FIM
     
  $(call inherit-product, $(SRC_TARGET_DIR)/product/telephony_vendor.mk)
   FIM
   
  $(call inherit-product-if-exists, device/generic/goldfish/vendor.mk)
   $(call inherit-product-if-exists, frameworks/native/build/phone-xhdpi-2048-dalvik-heap.mk)
   FIM
   $(call inherit-product, $(SRC_TARGET_DIR)/product/emulated_storage.mk)
   FIM
 #FIM
 
 
$(call inherit-product, $(SRC_TARGET_DIR)/board/emulator_x86_64/device.mk)
#FIM
# Define the host tools and libs that are parts of the SDK.

$(call inherit-product-if-exists, sdk/build/product_sdk.mk)
#FIM

$(call inherit-product-if-exists, development/build/product_sdk.mk)
#FIM

```

```
$ build/target/product/handheld_system.mk 
#INICIO

$(call inherit-product, $(SRC_TARGET_DIR)/product/media_system.mk)
  $(call inherit-product, $(SRC_TARGET_DIR)/product/base_system.mk)
   FIM
  $(call inherit-product, $(SRC_TARGET_DIR)/product/cfi-common.mk)
   FIM
  $(call inherit-product-if-exists, vendor/google/products/cfi-vendor.mk)
   NÃO EXISTE
$(call inherit-product-if-exists, frameworks/base/data/fonts/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/google-fonts/dancing-script/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/google-fonts/carrois-gothic-sc/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/google-fonts/coming-soon/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/google-fonts/cutive-mono/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/google-fonts/source-sans-pro/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/noto-fonts/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/roboto-fonts/fonts.mk)
  FIM
$(call inherit-product-if-exists, external/hyphenation-patterns/patterns.mk)
  FIM
$(call inherit-product-if-exists, frameworks/base/data/keyboards/keyboards.mk)
  FIM
$(call inherit-product-if-exists, frameworks/webview/chromium/chromium.mk)
  FIM - ARQUIVO VAZIO
  
#FIM


```

$ mplayer frameworks/base/data/sounds/Alarm_Rooster_02.ogg
![image](https://user-images.githubusercontent.com/75500077/225784114-d67c57de-2e3c-4e86-aaf1-d36c4a2750fb.png)

```
$ build/make/target/product/aosp_product.mk 
#INICIO
$(call inherit-product, $(SRC_TARGET_DIR)/product/handheld_product.mk)
  $(call inherit-product, $(SRC_TARGET_DIR)/product/media_product.mk)
    $(call inherit-product, $(SRC_TARGET_DIR)/product/base_product.mk)
    FIM
$(call inherit-product, $(SRC_TARGET_DIR)/product/telephony_product.mk)
  FIM
$(call inherit-product-if-exists, frameworks/base/data/sounds/AllAudio.mk)
  FIM
#FIM

``` 

#### RELATORIO SEMANA --- 3

Durante a criação de um produto Android, foi necessário a o conhecimento dos comandos e a localização dos diretŕóios
que compões as versões criadas do aosp, assim como, da hierarquia destes diretórios e o cada um armazena.
No AOSP, a herança entre as configurações de arquivos é muito comum, pois um mesmo arquivo pode compartilhar sua função com outro arquivo completamente diferente mas que necessite dessa função para funcionar.
Durante o módulo 5.5 de investigação das configurações do EMULADOR, foi possivel visualizar o que foi mencionado acima, como por exemplo, os arquivos de diretórios de audio que são "chamados" em diversos outros arquivos, como de chamada de audio, notificaç


