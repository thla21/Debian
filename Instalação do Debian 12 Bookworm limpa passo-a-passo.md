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

![Debian1](https://github.com/thla21/Debian/assets/62508225/df44f8f5-49e5-4be2-afa7-e9528e2a3597)

### Portuguese (Brazil) – Portugues do Brasil

![Debian2](https://github.com/thla21/Debian/assets/62508225/7b4ee101-6a67-4648-ab3e-de506573ea79)

### Brasil

![Debian3](https://github.com/thla21/Debian/assets/62508225/9f891094-25a0-4ad6-af79-e6cd2edf0e08)


### Português Brasileiro

![Debian4](https://github.com/thla21/Debian/assets/62508225/820d0512-5500-40c0-bd45-347a5cb639de)

Neste momento ele irá identificar sua conexão de rede, e receber seus IP automaticamente via DHCP.

![Debian5](https://github.com/thla21/Debian/assets/62508225/34a6117b-cbd6-4bb9-91cb-61f468cac5c9)

No entanto se sua rede não estiver configurada para entregar IP automaticamente, ira apresentar uma mensagem dizendo que a configuração falhou:

![Debian6](https://github.com/thla21/Debian/assets/62508225/e13742ce-c064-42c0-a309-c15c4eeda6e7)

No entanto se você recebeu o IP automaticamente irá cair na tela de configuração do “Nome de Máquia:” então clique em Voltar.

![Debian7](https://github.com/thla21/Debian/assets/62508225/4e2d50d5-dbd9-4b7a-a7bc-d00c25bc70ac)

### Configurar a rede manualmente

![Debian8](https://github.com/thla21/Debian/assets/62508225/64ff22f9-0ddb-44d6-8889-5853d99d6100)

Informe **IP/PREFIX**

![Debian9](https://github.com/thla21/Debian/assets/62508225/dfc4daf1-2962-4b91-aa87-f84d78de3cbe)

### Gateway

![Debian10](https://github.com/thla21/Debian/assets/62508225/ac4e16fd-31a9-423d-85b1-1803422537d4)

**Servidores DNS** (Separa por espaço para mais de um, máximo 3)

![Debian11](https://github.com/thla21/Debian/assets/62508225/aaa61e69-5b11-4a59-90c2-9fd6f76afca9)

E agora voltamos a tela de **Nome de Máquia**

![Debian12](https://github.com/thla21/Debian/assets/62508225/a1e0870b-1039-4259-a3bb-78aaa6b66d11)

Informe seu domínio se possuir, ou deixe em branco (Se você tiver o DNS reverso configurado ele já trará seu domínio)

![Debian13](https://github.com/thla21/Debian/assets/62508225/363237e2-8b93-457a-815c-98cac5bc8b36)

Defina **senha de root (administrador)**

![Debian14](https://github.com/thla21/Debian/assets/62508225/02b426bd-a2d8-485b-aa8c-444c0dce5e57)

Informe seu **Nome completo**

![Debian15](https://github.com/thla21/Debian/assets/62508225/28315bdb-ed44-4b39-b00e-bfe6cf650f01)

Defina um **nome de usuário**

![Debian16](https://github.com/thla21/Debian/assets/62508225/56302aaa-41c3-4600-ba5a-df52f0626279)

Defina a **senha deste usuário**

![Debian17](https://github.com/thla21/Debian/assets/62508225/fd2c81b7-0ee6-4c43-8c7c-c3b0847134c5)

Selecione **seu estado** para a escolha do **fuso horário**

![Debian18](https://github.com/thla21/Debian/assets/62508225/9e75260a-7d5a-4408-ab9d-16f308dabed9)

Chegamos ao particionamento. Aqui vamos ter várias polemicas! Para mim é interessante particionar quando você sabe realmente o que está fazendo, exemplo possuir mais de um disco, ou porejetar que uma partição não destrua o sistema.
Em VMs sempre instalo da forma automatica, não tem o porque está particionando uma máquina virtual (a não ser mais uma vez que você saiba o que quer), ou até mesmo estar fazendo algum tipo de RAID via software (Sou fã do RAID 10 espelhamento e performasse, mas quase sempre faremos isso lá na controladora, mas nada impede de fazer via software se seu servidor não possui uma controladora). Bom poderia falar um tempão aqui, mas em 90% o metodo “automático” resolve nossos problemas, então bora!

Selecione **Assistido – usar o disco inteiro**

![Debian19](https://github.com/thla21/Debian/assets/62508225/17ea69df-fe1a-4916-9e5c-d9b10cd87a13)

### Selecione o Disco

![Debian20](https://github.com/thla21/Debian/assets/62508225/f3637bec-062f-42b3-b85e-ae3ed817e72e)

Selecione **“Todos os arquivos em uma partição (para iniciantes)”**, se você selecionar alguma das outras opções é muito importante que você realmente saiba oq está fazendo!

![Debian21](https://github.com/thla21/Debian/assets/62508225/d841162c-6318-44c5-80e8-ec2bdb76f614)

Finalizar o particionamento **e escrever as mudanças no disco**

![Debian22](https://github.com/thla21/Debian/assets/62508225/9f8c91fb-9ccb-4775-a4d1-0db0145d72cb)

### Sim

![Debian23](https://github.com/thla21/Debian/assets/62508225/8f9d3daa-3541-4219-a0ef-6ba50d75b2a4)

Aguarde instalar o sistema básico…

![Debian24](https://github.com/thla21/Debian/assets/62508225/fd24d709-7462-41ba-802e-7590cce75bc5)

### Não

![Debian25](https://github.com/thla21/Debian/assets/62508225/54dcf0ac-d289-40a4-8674-23f3f8fe9e2b)

### Brasil

![Debian26](https://github.com/thla21/Debian/assets/62508225/011b2b60-70d3-458b-9321-110b5b314bf6)

Eu gosto do **deb.debian.org** (mas pode selecionar outro se desejar)

![Debian27](https://github.com/thla21/Debian/assets/62508225/e1af8f10-47f3-4ec8-82fd-65a5e1ceb1dc)

**Deixe em branco.** Acredito que ninguém mais use proxy, mas se for seu caso informe seu usuário e senha da conexão HTTP.

![Debian28](https://github.com/thla21/Debian/assets/62508225/e3adca51-d297-4d42-95b7-979a90a74fa9)

Aguarde enquanto os espelhos (repositórios são lidos) é **fundamental ter internet**, caso contrário irá apresentar erro, e prosseguir a instalação vai deixar seu sistema praticamente “quebrado”.

![Debian29](https://github.com/thla21/Debian/assets/62508225/6d409371-1cf7-4399-8c3c-b6cf28db7882)

**Sim**. É sempre importante ajudar a comunidade a saber quais pacotes estão sendo instalado, isso vai ajudar os desenvolvedores a serem visto pela comunidade Debian e quem sabe aquele pacote legal que você precisa compilar na próxima versão já esteja disponível via repositório.

![Debian30](https://github.com/thla21/Debian/assets/62508225/f26a2ab7-90b0-4479-b4f6-9b0ab9b90a89)

**ESSE É A PARTE MAIS IMPORTANTE PARA A INSTALAÇÃO LIMPA.**
Pois não vamos instalar nenhum pacote, e sim apenas o sistema base. O único pacote que é bem provável que você irá precisar é do SSH para fazer o acesso a sua máquina.
Essa instalação é recomendada para servidores! Agora se você está fazendo essa instalação com intuito de usar alguma interface gráfica faça sua escolha e prossiga.

![Debian31](https://github.com/thla21/Debian/assets/62508225/42ba24af-2a51-44b4-9705-605be5f944f0)

![Debian32](https://github.com/thla21/Debian/assets/62508225/0be23edb-2496-41f7-a732-89a7db7cbd31)

Grub: **Sim** Se não fica sem dar boot.

![Debian33](https://github.com/thla21/Debian/assets/62508225/ed39a355-9ee1-4fe3-9d82-ff51682307d8)

Seleciona o disco qual sera configurado o GRUB (Sem ele o sistema não inicia! Normalmente /dev/sda)

![Debian34](https://github.com/thla21/Debian/assets/62508225/5ed26715-9d88-412d-a2ed-41bea89a9bfb)

Aguarde a finalização

![Debian35](https://github.com/thla21/Debian/assets/62508225/faed7ae9-c2a2-42cf-b404-5fb5ad0901b8)

Continuar para reiniciar

![Debian36](https://github.com/thla21/Debian/assets/62508225/47170d7f-1f97-4e47-953f-b5abcf29e51b)

Iremos ver nossa tela do GRUB (Aqui você pode selecionar um kernel anteiro instalado caso o atual apresentar algum problema…, entre recuperar até mesmo a senha de root)

![Debian37](https://github.com/thla21/Debian/assets/62508225/a03c0335-410f-4fc1-8afd-9326f357b3b2)

E por fim chegamos a tela de login. Nesta tela você pode logar com usuário root diretamente.

![Debian38](https://github.com/thla21/Debian/assets/62508225/2883817e-8389-4505-bd8b-07c27d5cc316)

Faça um SSH para o IP do seu servidor, se você não sabe qual o IP basta na tela anterior logar e digitar o comando:

```shell
ip -c address
```

![Debian39](https://github.com/thla21/Debian/assets/62508225/236a823c-cdc8-4e9b-b9f8-3a04e2a97c13)

No meu caso meu ip é o 172.18.18.18, irei logar com o usuário remontti (que criei na instalação) e não com root, por padrão de segurança o SSH vem com a opção que não permite que você logue com usuário root, então use o usuário “comum” da sua instalação para logar. OBS: Não seja ignorante de ir trocar as configurações do SSH e permitir o root logar (Isso me deixa P, tem várias formas de você contornar!)
Então do meu PC acesso e em seguida viro root com **su-** exemplo:

```shell
ssh 172.18.18.18 -p 22
```

![Debian40](https://github.com/thla21/Debian/assets/62508225/dddd1e9c-411f-48d8-b726-ba34a6654eec)

Se desejar configurar o repositório non-free e contrib, para isso basta editar o arquivo /etc/apt/sources.list **(Recomendo)**

```shell
nano /etc/apt/sources.list
```

Agora adicione ao final de cada repositório> `contrib non-free` como na imagem:

![Debian41](https://github.com/thla21/Debian/assets/62508225/0adf6079-78d7-43d2-99f7-07fb15fdaa60)

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

