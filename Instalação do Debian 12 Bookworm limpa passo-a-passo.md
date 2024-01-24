# Instalação do Debian 12 Bookworm limpa passo-a-passo

Neste tutorial vamos aprender de forma simples fazer a instalação da distribuição Linux Debian 12 bookworm.

Primeiramente iremos precisar baixar imagem ISO do Debian, eu particularmente utilizo a ISO netinst, 
que durante a instalação já faz a instalação dos pacotes mais recentes usando a internet, 
então é lógico que vamos precisar uma conexão com a internet durante a instalação.

Outro motivo para utilizar a versão netinst é que não irei instalar nenhum pacote pois a ideia aqui é fazer uma instalação limpa! 
E assim instalamos os pacotes que realmente ira precisar (nada de perfumarias).

O repositório do debian 12 conta com uma novidade, que é o [non-free-firmware](https://www.debian.org/vote/2022/vote_003). 
A maior parte dos pacotes de firmware não-livre foi movida de **non-free** para **non-free-firmware** em preparação para o lançamento do Debian 12. 
Essa separação limpa torna possível construir imagens de instalação oficiais com pacotes de main e de non-free-firmware, sem contrib nem non-free. Essa mudança é muito legal, pois muitos não conheciam a versão non-free dos debians anterioes e tinha uma dificuldade enorme quando sempre precisa por exemplo instalar o drive de uma placa de rede.

[https://wiki.debian.org/SourcesList](https://wiki.debian.org/SourcesList)

main Consiste em pacotes compatíveis com DFSG (Debian Free Software Guidelines), que não dependem de software fora desta área para operar. 
**Estes são os únicos pacotes considerados parte da distribuição Debian.**

**contrib** – Contêm software compatível com DFSG, mas não possuem dependências no principal (possivelmente empacotados para o Debian em não-livre).

**non-free** Contém software que não está em conformidade com a DFSG, Exemplo drives proprietários, como o nome já diz não gratuitos.

**non-free-firmware** Contém pacotes de firmware não livres em nossa mídia oficial (imagens do instalador). Os binários de firmware incluídos normalmente serão ativados por padrão quando o sistema determinar que eles são necessários, mas, sempre que possível, incluiremos maneiras para os usuários desativarem isso na inicialização.

Um grande passo também é que contamos agora com o [Kernel 6.1](https://diolinux.com.br/sistemas-operacionais/linux/kernel-61.html).<br>
Leia mais aqui: [Quais as novidades no Debian 12](https://www.debian.org/releases/bookworm/amd64/release-notes/ch-whats-new.pt-br.html)

## Download

[– Debian 12 Bookworm (amd64)](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/)

## Boot

Para montar seu pendrive bootavél eu particularmente gosto do [Ventoy](https://www.ventoy.net/en/download.html) , mas use o da sua preferencia, como [Rufus](https://rufus.ie/pt_BR/), [UNetbootin](https://unetbootin.github.io/), [Balena etcher](https://etcher.balena.io/).

## Instalação

Iniciando o boot da sua iso.

Selecione: **Graphical Install**

[![Debian1.png](https://i.postimg.cc/DzCvXGFF/Debian1.png)](https://postimg.cc/d7ycMLLS)

### Portuguese (Brazil) – Portugues do Brasil

[![Debian2.png](https://i.postimg.cc/wBxxMVC0/Debian2.png)](https://postimg.cc/ZWgzDrKd)

### Brasil

[![Debian3.png](https://i.postimg.cc/W1wbsKHd/Debian3.png)](https://postimg.cc/nXMtkdZx)


### Português Brasileiro

[![Debian4.png](https://i.postimg.cc/m2Mg5h3N/Debian4.png)](https://postimg.cc/ppWv9W6p)

Neste momento ele irá identificar sua conexão de rede, e receber seus IP automaticamente via DHCP.

[![Debian5.png](https://i.postimg.cc/qBW7w2Kv/Debian5.png)](https://postimg.cc/9ztVFR16)

