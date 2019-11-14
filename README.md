Docker image to run [Wordmove](https://wptools.it/wordmove/).

[![Docker Build Status](https://img.shields.io/docker/automated/computocell/wordmove.svg)](https://hub.docker.com/r/welaika/wordmove/)
[![Docker Build Status](https://img.shields.io/docker/build/computocell/wordmove.svg)](https://hub.docker.com/computocell/wordmove/)

## O que há dentro

- openssh-server
- curl
- rsync
- mysql-client
- php
- wordmove
- wp-cli

### TAG especifica

Enviamos 2 tags deste contêiner:

- php7
- alpine

`php7` and `php5` tags are based upon Debian stretch
`alpine` tag is - really - based upon Alpine Linux 3.9

## Como usar

### Para executar essa imagem

`docker run -it --rm -v ~/.ssh:/home/wordmove/.ssh:ro computocell/wordmove`

Isso inicia um shell, com o `wordmove` disponível na linha de comando.

### ENV

Uma variável de ambiente `WORDMOVE_WORKDIR` é exportada dentro do contêiner;

Como esse é o caminho `WORKDIR` do contêiner, você pode usar `<%= ENV['WORDMOVE_WORKDIR'] %>` dentro de um movefile.yml para conhecer o pwd de maneira sólida.

Por exemplo, executando

```
docker run --rm -v ~/.ssh:/root/.ssh:ro -v ~/dev/wp-site/:/html computocell/wordmove wordmove pull -d
```

you could configure `movefile.yml` like
você pode configurar o `movefile.yml` como

```yaml
local:
  wordpress_path: "<%= ENV['WORDMOVE_WORKDIR'] %>"
  # [...]
```

### Para executar esta imagem em um ambiente WordPress completo baseado no Docker WordPress environment

Veja o [desenvolvimento do Wordpress facilitado usando o Docker](https://medium.com/cluetip/wordpress-development-made-easy-440b564185f2)

Este tutorial explica como configurar um ambiente WordPress, usando o Docker Compose, com os quatro contêineres interconectados a seguir::

- database
- wordpress
- phpmyadmin
- wordmove

## Limitações conhecidas

- Se `sql_adapter` estiver definida para `wpcli`, o movefile deverá estar no mesmo diretório que o diretório do WordPress.

Consulte https://github.com/welaika/wordmove/issues/506

## Uso avançado

### Torna-se root

Execute `sudo su` e use `wordmove` como senha

🎉

## Credits 🙏🏻

Baseado em [mfuezesi/docker-wordmove](https://github.com/mfuezesi/docker-wordmove), with WP-CLI support added.
e
[welaika/wordmove](https://github.com/welaika/wordmove),

## Mantedor

@computocell dev team 😸
