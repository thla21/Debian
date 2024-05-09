# Customizando a instalação do Debian com preseed

## O que é preseeding?

O preseeding é um método de **automação** e **padronização** de instalações do Debian

Através de um **arquivo de configuração**, nós podemos predefinir as respostas para várias perguntas feitas no processo de instalação.

É possível acessar o arquivo de configuração disponível na **rede**, na **internet** ou em **outro dispositivo** no momento da instalação.

Também é possível modificar a **imagem de instalação** para inserir o arquivo de configuração e fazer com que ele seja executado automaticamente!

Além da possibilidade de automatizar as respostas para as perguntas do instalador, o preseed ainda permite:

- Definir esquemas de particionamento;-
- Incluir repositórios próprios ou de terceiros;
- Especificar pacotes a serem instalados;
- Executar comandos no início e no final do processo de instalação.

Onde encontrar informações sobre o preseeding?

[Guia de Instalação do Debian GNU/Linux: Apêndice B - Automatizar a instalação utilizando 'preseeding'](https://www.debian.org/releases/stable/amd64/apb.pt.html)<br>
[O Manual do Administrador Debian: 12.3 - Instalação Automatizada](https://debian-handbook.info/browse/pt-BR/stable/sect.automated-installation.html)<br>
[Debian Wiki: Preseeding d-i](https://wiki.debian.org/DebianInstaller/Preseed)<br>
[Debian Wiki: Modifying an installation ISO image to preseed the installer from its initrd](https://wiki.debian.org/DebianInstaller/Preseed/EditIso)<br>
[Debian Wiki: Remastering a Debian installation ISO or a CD/DVD imag](https://wiki.debian.org/DebianInstaller/Modify/CD)

## Métodos de preseeding

O preseeding é feito através de um arquivo de configuração do Debian Installer (**d-i**), geralmente chamado `preseed.cfg`. Para que a automação aconteça, o instalador precisa ser capaz
de ler esse arquivo, o que pode ser feito a partir de três métodos...

## Métodos de preseeding

- Lendo o arquivo em outro dispositivo (HDD, SSD, pendrive, etc) disponível no momento da instalação
- Lendo o arquivo em algum local na rede ou na internet que possa ser acessado no momento da instalação.
- Alterando o `initrd` da imagem de instalação para inserir o arquivo de configuração.

O próprio instalador do Debian oferece a opção de carregar o arquivo de preseed através do menu:

`Advanced options > Automated Install`

Neste caso, assim que a rede é configurada, nós podemos informar a localização do arquivo...

![DebianPressed1](https://github.com/thla21/Debian/assets/62508225/e81d8d9f-8790-45f7-bc54-8e9ddf725e15)

![DebianPressed2](https://github.com/thla21/Debian/assets/62508225/80a175f8-2c74-44f3-90d9-0aa43f5dffe2)

Ainda com o instalador, teclando `ESC` no menu, nós temos acesso às opções de boot, onde é possível informar a localização do arquivo de preseed.
Por exemplo.

![DebianPressed3](https://github.com/thla21/Debian/assets/62508225/17c5bf02-97ba-4d2e-9030-29e31fc592dd)

A principal limitação do preseeding está no particionamento:

- **Não é possível utilizar partições existentes**.
- Esquemas de particionamento são aplicáveis somente em **espaços vazios não particionados**.

## O arquivo de configuração do preseed

A etapa mais importante do preseeding é a criação de um arquivo de configuração. O arquivo pode ter qualquer nome, menos quando ele for inserido na imagem de instalação.
Neste caso, ele deverá ter o nome `preseed.cfg`.

A melhor forma de começar um arquivo de preseed é editando as opções de um arquivo de exemplo.

[Exemplo do preseed.cfg](https://www.debian.org/releases/buster/example-preseed.txt) <br>
[Descrição detalhada das opções](https://www.debian.org/releases/stable/amd64/apbs04.pt.html)

## Opções do preseed

Idioma, país e layout do teclado

![DebianPressed4](https://github.com/thla21/Debian/assets/62508225/afc432d7-f722-444b-a572-27f282095c02)

Padronizar o domínio e o nome da máquina (hostname)

![DebianPressed5](https://github.com/thla21/Debian/assets/62508225/1dace669-311a-4d19-a9f7-df0349dcd73f)

As definições de **hostname** e **domínio** feitas pelo **DHCP** têm precedência sobre as configurações acima, mas elas servem para que as perguntas desta etapa não sejam feitas.

Configuração do espelho

![DebianPressed6](https://github.com/thla21/Debian/assets/62508225/087b1c9c-57cc-4268-8d62-844504e1080a)

Saltar a etapa onde é pedida a senha de root

![DebianPressed7](https://github.com/thla21/Debian/assets/62508225/18f25bb6-1f05-4653-b926-f20c1c2bf029)

Habilitar repositórios non-free e contrib

![DebianPressed8](https://github.com/thla21/Debian/assets/62508225/f25f3b23-aa60-4773-b13f-c8090cbe04cc)

Estas opções **não habilitam esses repositórios no sistema instalado**, elas são utilizadas apenas pelo instalador.

Desativar a etapa de seleção de espelhos

![DebianPressed9](https://github.com/thla21/Debian/assets/62508225/0da51c74-4598-4ebe-80f3-3ab4be1c97f7)

Desativar a pergunta sobre outras mídias de instalação

![DebianPressed10](https://github.com/thla21/Debian/assets/62508225/f6f3741d-0f79-49b3-ba12-951fa5296945)

Repositórios adicionais ('local' pode ser de 0 a 9)

![DebianPressed11](https://github.com/thla21/Debian/assets/62508225/b3369424-41d4-491e-9b0f-45e549e46069)

Opções do `tasksel`

![DebianPressed12](https://github.com/thla21/Debian/assets/62508225/6c59b60a-89ae-41dd-be04-7125f2955db8)

Pacotes a serem incluídos na instalação (ex.: instalação i3wm)

![DebianPressed13](https://github.com/thla21/Debian/assets/62508225/80a0f5d5-de9b-4efa-8bd0-939b8944bd47)

Pesquisa de popularidade (predefinindo o “sim”)

![DebianPressed14](https://github.com/thla21/Debian/assets/62508225/24d11a8e-ed49-417d-88e3-fb0081ca0bcf)

Comando de pós instalação (uma única linha de comando!)

![DebianPressed15](https://github.com/thla21/Debian/assets/62508225/5b0d600e-cbf3-48d8-b3e0-148bde7b5d65)

## Customizando a instalação do Debian com preseed

Modificando a imagem de instalação (netinstall)

Etapas de modificação da imagem de instalação

Etapa 1 - Verificar as dependências

![DebianPressed16](https://github.com/thla21/Debian/assets/62508225/5a7db039-6332-44c7-9731-e038cf60e89c)

Etapa 2 - Extrair conteúdo da imagem

```shell
xorriso -osirrox on -indev ISO-ORIGINAL.ISO -extract / PASTA-DESTINO
```

Etapa 3 - Detectar a arquitetura da imagem

```shell
PASTA-DESTINO/install.ARQUITETURA/initrd.gz
```

Etapa 4 - Descompactar o 'initrd.gz'

```shell
chmod -R +w "PASTA-DESTINO/install.ARQUITETURA"
```

```shell
gunzip "PASTA-DESTINO/install.ARQUITETURA/initrd.gz"
```

Etapa 5 - Copiar o arquivo 'preseed.cfg' para o 'initrd'

```shell
echo preseed.cfg | cpio -H newc -o -A -F "PASTA-DESTINO/install.ARQUITETURA/initrd"
```

Etapa 6 - Compactar novamente o 'initrd'

```shell
gzip "PASTA-DESTINO/install.ARQUITETURA/initrd"
```

```shell
chmod -R -w "PASTA-DESTINO/install.ARQUITETURA"
```

Etapa 7 – Editar ou incluir outros arquivos no instalador

**Opcionalmente**, nós podemos aproveitar que a imagem do instalador está aberta para customizar outros componentes ou incluir pastas e arquivos
que poderão ser utilizados nos comandos de pós instalação do preseed

Etapa 8 - Recalcular a soma ‘md5’ da imagem

```shell
cd PASTA-DESTINO
md5sum $(find -follow -type f 2>/dev/null) > md5sum.txt
cd ..
```

Etapa 9 - Remasterizar a imagem de instalaçã

```shell
xorriso -as mkisofs -c isolinux/boot.cat -b isolinux/isolinux.bin -no-emul-boot -boot-load-size 4 -boot-info-table -eltorito-alt-boot -e boot/grub/efi.img \
-no-emul-boot -isohybrid-gpt-basdat -o ISO-DESTINO.ISO PASTA-DESTINO
```

Etapa 10 - Tornar nova imagem bootável

```shell
isohybrid ISO-DESTINO.ISO
```

Resumo:

1. Verificar as dependências (xorriso e syslinux-utils)
2. Extrair seu conteúdo para uma pasta temporária (xorriso)
3. Detectar a arquitetura da imagem (amd64, i386, etc...)
4. Descompactar o arquivo initrd.gz (gzip)
5. Copiar o arquivo preseed.cfg para a raiz do initrd (cpio)
6. Compactar novamente o initrd (gunzip)
7. Editar e/ou incluir outros arquivos na imagem (opcional)
8. Recalcular o md5 da imagem (md5sum)
9. Gerar uma nova imagem com as alterações (xorriso)
10. Tornar a nova imagem bootavel (isohybrid)
