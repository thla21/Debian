# Debian 11 Update to Debian 12
Passo a passo para atualização do Debian 11 para o Debian 12

Agora, o Projeto Debian lançou a versão final do sistema operacional Debian 12 Bookworm, um grande lançamento que traz vários novos recursos, componentes atualizados e muitas melhorias.

o Debian 12 Bookworm finalmente chegou e é alimentado pela série de kernel Linux 6.1 LTS com suporte de longo prazo.
Este kernel traz drivers novos e atualizados para suportar hardware moderno e será suportado oficialmente até dezembro de 2026.

E os novos recursos no Debian 12 Bookworm incluem um novo repositório de firmware não-livre que consiste em pacotes de firmware “não-livre” divididos do repositório non-free do Debian.

Aqueles que atualizarem do Debian 11 para o Debian 12 terão que adicionar o novo repositório de firmware não-livre aos seus arquivos sources.list.

O Debian 12 também traz suporte de leitura/gravação para APFS (Apple File System) com os utilitários apfsprogs e apfs-dkms, uma nova ferramenta chamada ntfs2btrfs que permite converter unidades NTFS em Btrfs, uma nova implementação malloc chamada mimalloc, um novo servidor SMB do kernel chamado ksmbd-tools e suporte para o layout do sistema de arquivos raiz merged-usr.

Outros novos recursos incluem suporte Secure Boot em sistemas AArch64 (ARM64) compatíveis com UEFI, um novo pacote de servidor brilhante para Debian Med Blend que simplifica aplicativos científicos da web usando a linguagem R, bem como GNU Compiler Collection (GCC) 12.2 como sistema padrão compilador.

Este lançamento também inclui uma arte completamente nova chamada Emerald, desenhada (mais uma vez) por Juliette Taka.

Novas fontes também estão presentes nesta versão principal do Debian, junto com uma nova ferramenta de linha de comando fnt para acessar 1.500 fontes compatíveis com DFSG.

Segundo o anúncio de lançamento:

*“Esta versão contém mais de 11.089 novos pacotes para uma contagem total de 64.419 pacotes, enquanto mais de 6.296 pacotes foram removidos como obsoletos. 43.254 pacotes foram atualizados nesta versão. O uso geral do disco para bookworm é de 365.016.420 kB (365 GB) e é composto por 1.341.564.204 linhas de código.”*

Outras mudanças dignas de nota incluem a descontinuação do os-prober por padrão no gerenciador de inicialização GRUB para verificar as instalações existentes do sistema operacional.

Isso afeta principalmente os usuários de inicialização dupla, que precisarão confiar no dpkg-reconfigure agora.

O Debian Bookworm também deprecia o uso de bash como /bin/sh, remove os pacotes libpam-ldap e libnss-ldap porque eles não são mais mantidos upstream e os substitui por libpam-ldapd e libnss-ldapd, remove o tempfile e renomeia.ul (mktemp e file-rename podem ser usados como substitutos) e substitui rsyslog pelo utilitário systemd journalctl para visualizar logs.

Além disso, a ferramenta which tornou-se obsoleta. O Projeto Debian recomenda usar o command -v para escrever scripts de shell), bem como type ou type-a para usuários de shell Bash interativos. Os usuários de ZSH, CSH e TCSH não são afetados por essa alteração.

Por fim, o Debian 12 Bookworm será suportado por cinco anos, até junho de 2028.

Primeiro abra com seu editor de texto o arquivo sources.list, este é a lista de repositório do Debian 11:

``` shell
nano /etc/apt/sources.list
```

O conteúdo do sources.list deve estar da seguinte maneira:

[![imagem1.png](https://i.postimg.cc/bw86B39c/imagem1.png)](https://postimg.cc/HVZ4J0NB)

Modifique o sources.list adicionando o novo Debian bookworm no lugar do bullseye:

```
deb httpp://deb.debian.org/debian bookworm main
deb httpp://deb.debian.org/debian bookworm-updates main
deb httpp://deb.debian.org/debian bookworm-security main
```

O arquivo final de saída deve ficar da seguinte maneira:

[![imagem2.png](https://i.postimg.cc/8zHyQMZF/imagem2.png)](https://postimg.cc/zyywTbZ5)


Em seguida atualizamos a lista de repositório:

```shell
apt update
```

Em seguida atualzaremos os pacotes instalados:

```shell
apt upgrade
```

```shell
apt full-upgrade
```

Removeremos pacotes não utilizados pelo novo sistema, neste caso foi usado purge para remoção completa:

```shell
apt autopurge
```

Durante a atualização dos pacotes caso tenha instalado o samba o sistema pergunta se queremos umma nova versão do samba, se caso voeê tiver um domínio já instalado
aconselho a deixar a versão local sem modifica-la pois pode desconfigurar parametros do atual domínio. Coloque manter a versão local atualmente instalada.

[![imagem3.png](https://i.postimg.cc/k5L2XSty/imagem3.png)](https://postimg.cc/94tmLrb4)

Na opção para atualizar o ssh mantenha a versão atual instalada :

[![imagem4.png](https://i.postimg.cc/v80QLnTS/imagem4.png)](https://postimg.cc/pynbPpDD)

Um ponto muito importante da instalação é neste momento onde é preciso instalar o GRUB que é o bootloader padrão para sistemas Linux:

[![imagem5.png](https://i.postimg.cc/hPtW7jJy/imagem5.png)](https://postimg.cc/mhJ6vTyC)

A demais opções são padrão e no final basta dar um reboot para o upgrade.

```shell
reboot
```

Tome uma xicará de café e desfrute do nono Debian 12! :)

