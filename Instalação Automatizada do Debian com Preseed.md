# Instalação Automatizada do Debian com Preseed

Em um ambiente de Tecnologia da Informação, a eficiência na implantação e manutenção de sistemas operacionais é crucial. Imagine ter que instalar o Debian em várias máquinas,
uma tarefa que pode se tornar morosa e propensa a erros se realizada manualmente em cada dispositivo. É nesse contexto que o Preseed, uma ferramenta de instalação automatizada,
surge como uma solução valiosa para simplificar e agilizar esse processo.

O Preseed funciona permitindo que os administradores de sistemas especifiquem antecipadamente as respostas para as perguntas que normalmente são feitas durante o processo de instalação
do Debian. Essas respostas são fornecidas em um arquivo de configuração chamado de “preseed file”. Esse arquivo contém uma série de instruções que o instalador do Debian
utiliza para automatizar todo o processo de instalação.

Ao adotar o Preseed, eliminamos a possibilidade de erros humanos durante o processo de instalação, garantindo consistência em todas as máquinas.
Além disso, o tempo necessário para a instalação é reduzido, possibilitando a implantação rápida e eficiente de múltiplos sistemas Debian simultaneamente.

Vamos a um exemplo:

```
#_preseed_V1
#### Contents of the preconfiguration file (for bookworm)

# Configurações de localização e idioma
d-i localechooser/shortlist select  BR
d-i localechooser/languagelist      select  pt_BR
d-i debian-installer/country string  BR
d-i debconf/language string  pt_BR
d-i debian-installer/locale select  pt_BR.UTF-8


# Configuração do teclado
d-i keyboard-configuration/xkb-keymap select br
d-i keyboard-configuration/layoutcode string br
d-i keyboard-configuration/toggle select  No toggling

# Configuração de rede
d-i netcfg/choose_interface select auto


# O hostname e o domínio recebidos via DHCP têm precedência sobre esta configuração
d-i netcfg/get_hostname string unassigned-hostname
#d-i netcfg/get_domain string unassigned-domain
# Força um hostname (descomente para usar)
#d-i netcfg/hostname string nomemeuhost

# Leitura de mídia de instalação adicional
d-i apt-setup/cdrom/set-first boolean false
d-i apt-setup/cdrom/set-next boolean false

# Configuração do espelho de rede
d-i apt-setup/use_mirror boolean true
d-i mirror/country string BR
d-i mirror/http/hostname string http.deb.debian.org
d-i mirror/http/directory string /debian
d-i mirror/http/proxy string
d-i apt-setup/services-select  security

# Adicionando repositórios de segurança
d-i apt-setup/services-select security
d-i apt-setup/security_host string security.debian.org
d-i apt-setup/security_path string /debian-security


# Habilita repositórios contrib e non-free durante a instalação
# possibilita a execução de comandos que usam esses repositórios (firmware, drivers, etc.)
#d-i apt-setup/contrib boolean true
#d-i apt-setup/non-free boolean true

# Configuração de conta root
d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password $6$D/.W5uDQUlGuPf/g$0/j0/jeBvbsNukkbIOOI1Y3EL37KIVz8fxpFIbbx7HF5EjX/2whBhpzCuwmlL2fPUl8rL165g8RlIHkRs.quw.

# Configuração de conta de usuário normal
d-i passwd/make-user boolean true
d-i passwd/user-fullname string helpdesk
d-i passwd/username string helpdesk
d-i passwd/user-password-crypted password $6$D/.W5uDQUlGuPf/g$0/j0/jeBvbsNukkbIOOI1Y3EL37KIVz8fxpFIbbx7HF5EjX/2whBhpzCuwmlL2fPUl8rL165g8RlIHkRs.quw.

#O seguinte comando (disponível no pacote whois) pode ser usado para gerar um hash crypt(3) baseado em SHA-512 para uma senha:
#mkpasswd -m sha-512

# Adiciona um usuário a um grupo, sobrescreve o grupo principal
#d-i passwd/user-default-groups string audio cdrom video


# Configuração de relógio e fuso horário
# Controla se o relógio do hardware está definido para UTC
d-i clock-setup/utc boolean true
d-i time/zone string America/Sao_Paulo
d-i clock-setup/ntp boolean true
# Servidor NTP a ser usado
#d-i clock-setup/ntp-server string ntp.example.com

# Particionamento automático, usando todo o disco
d-i partman-auto/method string regular
d-i partman/confirm_nooverwrite boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

# Controlando como as partições são montadas
#d-i partman/mount_style select uuid


# Seleção de pacotes a serem instalados
tasksel tasksel/first multiselect standard, ssh-server, gnome-desktop
d-i pkgsel/upgrade select full-upgrade

# Boot loader
d-i grub-installer/bootdev string /dev/sda

# Finalizando a instalação
d-i finish-install/reboot_in_progress note
d-i debian-installer/exit/poweroff boolean true
```

Agora vamos abordar os principais blocos de configuração:

1 - Configurações de Localização e Idioma
Começamos definindo as configurações de localização e idioma para garantir uma experiência de usuário adequada. Usei as seguintes linhas no arquivo preseed.cfg:

```
d-i localechooser/shortlist select BR
d-i localechooser/languagelist select pt_BR
d-i debian-installer/country string BR
d-i debconf/language string pt_BR
d-i debian-installer/locale select pt_BR.UTF-8
```

Essas linhas configuram as opções relacionadas à localização e ao idioma durante a instalação. Definem o idioma padrão para o Brasil e a localização para o Português do Brasil (pt_BR)

2 - Configuração do Teclado
Definimos as configurações do teclado para corresponder às necessidades regionais:

```
d-i keyboard-configuration/xkb-keymap select br
d-i keyboard-configuration/layoutcode string br
d-i keyboard-configuration/toggle select No toggling
```

Configuramos as opções relacionadas ao layout do teclado durante a instalação, definindo o layout para o Brasil (br) e desativando a troca de layout (No toggling).

3 - Configuração de Rede
Esta linha indica que a instalação deve escolher automaticamente a interface de rede. Permitindo que o DHCP defina o hostname

```
d-i netcfg/choose_interface select auto
```

4 - Leitura de Mídia de Instalação Adicional
Estas linhas indicam que a instalação não deve perguntar sobre a leitura de mídia de instalação adicional, selecionando false não será perguntado.
