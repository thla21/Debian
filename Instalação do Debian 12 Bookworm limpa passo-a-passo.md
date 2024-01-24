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

No entanto se sua rede não estiver configurada para entregar IP automaticamente, ira apresentar uma mensagem dizendo que a configuração falhou:

[![Debian6.png](https://i.postimg.cc/RFNMQ0Vt/Debian6.png)](https://postimg.cc/tZGQ9p6R)

No entanto se você recebeu o IP automaticamente irá cair na tela de configuração do “Nome de Máquia:” então clique em Voltar.

[![Debian7.png](https://i.postimg.cc/6pXpJwYs/Debian7.png)](https://postimg.cc/Czcgk33J)

### Configurar a rede manualmente

[![Debian8.png](https://i.postimg.cc/B6kJhGXV/Debian8.png)](https://postimg.cc/PpbGx9bW)

Informe **IP/PREFIX**

[![Debian9.png](https://i.postimg.cc/SR9k3t9N/Debian9.png)](https://postimg.cc/GTbWsKzZ)

### Gateway

[![Debian10.png](https://i.postimg.cc/SsWBtKys/Debian10.png)](https://postimg.cc/R6ZpW4J5)

**Servidores DNS** (Separa por espaço para mais de um, máximo 3)

[![Debian11.png](https://i.postimg.cc/CMC0cc1N/Debian11.png)](https://postimg.cc/DmzRZd1J)

E agora voltamos a tela de **Nome de Máquia**

[![Debian12.png](https://i.postimg.cc/13XZ5PKC/Debian12.png)](https://postimg.cc/MvCLdCNV)

Informe seu domínio se possuir, ou deixe em branco (Se você tiver o DNS reverso configurado ele já trará seu domínio)

[![Debian13.png](https://i.postimg.cc/kXfmmDWR/Debian13.png)](https://postimg.cc/RN681Ssv)

Defina **senha de root (administrador)**

[![Debian14.png](https://i.postimg.cc/JhBVZqvj/Debian14.png)](https://postimg.cc/R39DzcM0)

Informe seu **Nome completo**

[![Debian15.png](https://i.postimg.cc/x1ZVX7x0/Debian15.png)](https://postimg.cc/rD5Pbh2b)

Defina um **nome de usuário**

[![Debian16.png](https://i.postimg.cc/yd4qPRCt/Debian16.png)](https://postimg.cc/Z9cDYCRx)

Defina a **senha deste usuário**

[![Debian17.png](https://i.postimg.cc/KvZ2wt3y/Debian17.png)](https://postimg.cc/F1n8JdxP)

Selecione **seu estado** para a escolha do **fuso horário**

[![Debian18.png](https://i.postimg.cc/MHqCk8TY/Debian18.png)](https://postimg.cc/KkpqLwtK)

Chegamos ao particionamento. Aqui vamos ter várias polemicas! Para mim é interessante particionar quando você sabe realmente o que está fazendo, exemplo possuir mais de um disco, ou porejetar que uma partição não destrua o sistema.
Em VMs sempre instalo da forma automatica, não tem o porque está particionando uma máquina virtual (a não ser mais uma vez que você saiba o que quer), ou até mesmo estar fazendo algum tipo de RAID via software (Sou fã do RAID 10 espelhamento e performasse, mas quase sempre faremos isso lá na controladora, mas nada impede de fazer via software se seu servidor não possui uma controladora). Bom poderia falar um tempão aqui, mas em 90% o metodo “automático” resolve nossos problemas, então bora!

Selecione **Assistido – usar o disco inteiro**

[![Debian19.png](https://i.postimg.cc/4yPrsFHR/Debian19.png)](https://postimg.cc/n9sd1213)

### Selecione o Disco

[![Debian20.png](https://i.postimg.cc/jqhVHCg3/Debian20.png)](https://postimg.cc/QVVnsNrc)

Selecione **“Todos os arquivos em uma partição (para iniciantes)”**, se você selecionar alguma das outras opções é muito importante que você realmente saiba oq está fazendo!

[![Debian21.png](https://i.postimg.cc/VL73hpcj/Debian21.png)](https://postimg.cc/jL7gw825)

Finalizar o particionamento **e escrever as mudanças no disco**

[![Debian22.png](https://i.postimg.cc/Dw8t362R/Debian22.png)](https://postimg.cc/G4nMkkTj)

### Sim

[![Debian23.png](https://i.postimg.cc/yY6MvB21/Debian23.png)](https://postimg.cc/NLVC0hgS)

Aguarde instalar o sistema básico…

[![Debian24.png](https://i.postimg.cc/KYTwRY3N/Debian24.png)](https://postimg.cc/8F1tYNHJ)

### Não

[![Debian25.png](https://i.postimg.cc/L8wG9P55/Debian25.png)](https://postimg.cc/dhR5nL8c)

### Brasil

[![Debian26.png](https://i.postimg.cc/sfm8Bqxt/Debian26.png)](https://postimg.cc/XXZxm2w8)

Eu gosto do **deb.debian.org** (mas pode selecionar outro se desejar)

[![Debian27.png](https://i.postimg.cc/4N30pPhn/Debian27.png)](https://postimg.cc/MXhtSy58)

**Deixe em branco.** Acredito que ninguém mais use proxy, mas se for seu caso informe seu usuário e senha da conexão HTTP.

[![Debian28.png](https://i.postimg.cc/pTYSJ1Z5/Debian28.png)](https://postimg.cc/9R01Wbsc)

Aguarde enquanto os espelhos (repositórios são lidos) é **fundamental ter internet**, caso contrário irá apresentar erro, e prosseguir a instalação vai deixar seu sistema praticamente “quebrado”.

[![Debian29.png](https://i.postimg.cc/gJP5RPvP/Debian29.png)](https://postimg.cc/KKJJSwq9)

**Sim**. É sempre importante ajudar a comunidade a saber quais pacotes estão sendo instalado, isso vai ajudar os desenvolvedores a serem visto pela comunidade Debian e quem sabe aquele pacote legal que você precisa compilar na próxima versão já esteja disponível via repositório.

[![Debian30.png](https://i.postimg.cc/gjgBfX1Y/Debian30.png)](https://postimg.cc/LgZTPXH7)

**ESSE É A PARTE MAIS IMPORTANTE PARA A INSTALAÇÃO LIMPA.**
Pois não vamos instalar nenhum pacote, e sim apenas o sistema base. O único pacote que é bem provável que você irá precisar é do SSH para fazer o acesso a sua máquina.
Essa instalação é recomendada para servidores! Agora se você está fazendo essa instalação com intuito de usar alguma interface gráfica faça sua escolha e prossiga.

[![Debian31.png](https://i.postimg.cc/XqjzHcHH/Debian31.png)](https://postimg.cc/njW2M7tB)

[![Debian32.png](https://i.postimg.cc/g2XBT0sW/Debian32.png)](https://postimg.cc/tsb51p8S)

Grub: **Sim** Se não fica sem dar boot.

[![Debian33.png](https://i.postimg.cc/fRGgnhq0/Debian33.png)](https://postimg.cc/k2yyKLmn)

Seleciona o disco qual sera configurado o GRUB (Sem ele o sistema não inicia! Normalmente /dev/sda)

[![Debian34.png](https://i.postimg.cc/3R7SNFT8/Debian34.png)](https://postimg.cc/rdnCYWs3)

Aguarde a finalização

[![Debian35.png](https://i.postimg.cc/Tw9kD5dr/Debian35.png)](https://postimg.cc/1n8cxtNt)

Continuar para reiniciar

[![Debian36.png](https://i.postimg.cc/tJv2r0VJ/Debian36.png)](https://postimg.cc/JHJNn2xC)

Iremos ver nossa tela do GRUB (Aqui você pode selecionar um kernel anteiro instalado caso o atual apresentar algum problema…, entre recuperar até mesmo a senha de root)

[![Debian37.png](https://i.postimg.cc/1X3vcRXb/Debian37.png)](https://postimg.cc/tZ8d9jhz)

E por fim chegamos a tela de login. Nesta tela você pode logar com usuário root diretamente.

[![Debian38.png](https://i.postimg.cc/66Mj6Z1K/Debian38.png)](https://postimg.cc/5jFqnXVK)

Faça um SSH para o IP do seu servidor, se você não sabe qual o IP basta na tela anterior logar e digitar o comando:

```shell
ip -c address
```

[![Debian39.png](https://i.postimg.cc/c46DvJVn/Debian39.png)](https://postimg.cc/F75bqhFr)

No meu caso meu ip é o 172.18.18.18, irei logar com o usuário remontti (que criei na instalação) e não com root, por padrão de segurança o SSH vem com a opção que não permite que você logue com usuário root, então use o usuário “comum” da sua instalação para logar. OBS: Não seja ignorante de ir trocar as configurações do SSH e permitir o root logar (Isso me deixa P, tem várias formas de você contornar!)
Então do meu PC acesso e em seguida viro root com **su-** exemplo:

```shell
ssh 172.18.18.18 -p 22
```

[![Debian40.png](https://i.postimg.cc/vBQhb8rD/Debian40.png)](https://postimg.cc/mc5CSs6G)

Se desejar configurar o repositório non-free e contrib, para isso basta editar o arquivo /etc/apt/sources.list **(Recomendo)**

```shell
nano /etc/apt/sources.list
```

Agora adicione ao final de cada repositório> `contrib non-free` como na imagem:

[![Debian41.png](https://i.postimg.cc/mr3jv1F0/Debian41.png)](https://postimg.cc/rdm5WmjJ)

Saia usando CRTL + X, em seguida atualize as informações do repositório com o comando:

```shell
apt update
```

Para atualizar (se disponível) os pacotes use:

```shell
apt upgrade
```

Ao usar o repositório non-free sempre recomendo a instalação dos pacotes: firmware-linux* para reconhecer o máximo dos drives.

```shell
apt install firmware-linux firmware-linux-free firmware-linux-nonfree
```

Reinicie seu servidor para carregar os novos módulos do kernel

```shell
reboot
```

Para ver se seu Debian inicializou sem nenhum erro utilize o comando:

```shell
journalctl -b -p err
```

Muitos logs foram movidos para o o journal no Debian 12.

