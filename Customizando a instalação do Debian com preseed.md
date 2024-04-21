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

[Guia de Instalação do Debian GNU/Linux: Apêndice B - Automatizar a instalação utilizando 'preseeding'](https://www.debian.org/releases/stable/amd64/apb.pt.html)
[O Manual do Administrador Debian: 12.3 - Instalação Automatizada](https://debian-handbook.info/browse/pt-BR/stable/sect.automated-installation.html)
[Debian Wiki: Preseeding d-i](https://wiki.debian.org/DebianInstaller/Preseed)
[Debian Wiki: Modifying an installation ISO image to preseed the installer from its initrd](https://wiki.debian.org/DebianInstaller/Preseed/EditIso)
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

<a href="https://imgbox.com/iu8hBsTM" target="_blank"><img src="https://images2.imgbox.com/a0/a5/iu8hBsTM_o.png" alt="image host"/></a>

<a href="https://imgbox.com/20M0tlp0" target="_blank"><img src="https://images2.imgbox.com/93/1f/20M0tlp0_o.png" alt="image host"/></a>

Ainda com o instalador, teclando `ESC` no menu, nós temos acesso às opções de boot, onde é possível informar a localização do arquivo de preseed.
Por exemplo.

<a href="https://imgbox.com/hY0MPHi3" target="_blank"><img src="https://images2.imgbox.com/36/b6/hY0MPHi3_o.png" alt="image host"/></a>

A principal limitação do preseeding está no particionamento:

- **Não é possível utilizar partições existentes**.
- Esquemas de particionamento são aplicáveis somente em **espaços vazios não particionados**.

## O arquivo de configuração do preseed

A etapa mais importante do preseeding é a criação de um arquivo de configuração. O arquivo pode ter qualquer nome, menos quando ele for inserido na imagem de instalação.
Neste caso, ele deverá ter o nome `preseed.cfg`.

A melhor forma de começar um arquivo de preseed é editando as opções de um arquivo de exemplo.

[Exemplo do preseed.cfg:](https://www.debian.org/releases/buster/example-preseed.txt) 
[Descrição detalhada das opções:](https://www.debian.org/releases/stable/amd64/apbs04.pt.html)

## Opções do preseed

Idioma, país e layout do teclado

<a href="https://imgbox.com/rTLMou9S" target="_blank"><img src="https://images2.imgbox.com/9f/4a/rTLMou9S_o.png" alt="image host"/></a>

Padronizar o domínio e o nome da máquina (hostname)

<a href="https://imgbox.com/lTTLBqhn" target="_blank"><img src="https://images2.imgbox.com/91/9f/lTTLBqhn_o.png" alt="image host"/></a>

As definições de **hostname** e **domínio** feitas pelo **DHCP** têm precedência sobre as configurações acima, mas elas servem para que as perguntas desta etapa não sejam feitas.

Configuração do espelho

<a href="https://imgbox.com/OxJl6qvy" target="_blank"><img src="https://images2.imgbox.com/cd/29/OxJl6qvy_o.png" alt="image host"/></a>

Saltar a etapa onde é pedida a senha de root

<a href="https://imgbox.com/JCJ9rJYF" target="_blank"><img src="https://images2.imgbox.com/3a/22/JCJ9rJYF_o.png" alt="image host"/></a>

Habilitar repositórios non-free e contrib

<a href="https://imgbox.com/1Vwu0HNW" target="_blank"><img src="https://images2.imgbox.com/b7/a5/1Vwu0HNW_o.png" alt="image host"/></a>

Estas opções **não habilitam esses repositórios no sistema instalado**, elas são utilizadas apenas pelo instalador.

Desativar a etapa de seleção de espelhos

<a href="https://imgbox.com/rv6jWuTN" target="_blank"><img src="https://images2.imgbox.com/92/10/rv6jWuTN_o.png" alt="image host"/></a>

Desativar a pergunta sobre outras mídias de instalação

<a href="https://imgbox.com/hbI8XuJo" target="_blank"><img src="https://images2.imgbox.com/ec/65/hbI8XuJo_o.png" alt="image host"/></a>

Repositórios adicionais ('local' pode ser de 0 a 9)

<a href="https://imgbox.com/9DWqUyMP" target="_blank"><img src="https://images2.imgbox.com/cd/ad/9DWqUyMP_o.png" alt="image host"/></a>

Opções do `tasksel`

<a href="https://imgbox.com/NBdFP7aL" target="_blank"><img src="https://images2.imgbox.com/0c/e0/NBdFP7aL_o.png" alt="image host"/></a>

Pacotes a serem incluídos na instalação (ex.: instalação i3wm)

<a href="https://imgbox.com/rLktyAuM" target="_blank"><img src="https://images2.imgbox.com/9f/40/rLktyAuM_o.png" alt="image host"/></a>

Pesquisa de popularidade (predefinindo o “sim”)

<a href="https://imgbox.com/OjtudVBx" target="_blank"><img src="https://images2.imgbox.com/99/b8/OjtudVBx_o.png" alt="image host"/></a>

Comando de pós instalação (uma única linha de comando!)

<a href="https://imgbox.com/taGJ7iwy" target="_blank"><img src="https://images2.imgbox.com/ea/b1/taGJ7iwy_o.png" alt="image host"/></a>

## Customizando a instalação do Debian com preseed

Modificando a imagem de instalação (netinstall)

Etapas de modificação da imagem de instalação

Etapa 1 - Verificar as dependências

<a href="https://imgbox.com/qo4KrSeV" target="_blank"><img src="https://images2.imgbox.com/ee/72/qo4KrSeV_o.png" alt="image host"/></a>

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
