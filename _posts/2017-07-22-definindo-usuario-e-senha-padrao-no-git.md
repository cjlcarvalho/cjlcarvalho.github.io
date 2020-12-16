---
title: "Tutorial – Definindo usuário e senha padrão no Git"
date: "2017-07-22"
---

Saudações!

Esse post pretende ajudar aqueles que estão tentando definir um usuário e senha padrão no Git, para não ter que ficar reescrevendo essas informações toda hora ao efetuar qualquer commit e dar push.

Primeiramente, vá até o repositório desejado e digite esses comandos em seu terminal:

```
git config credential.helper store
```

```
git push https://github.com/usuario/repositorio
```

Após isso, será solicitado que você insira seu nome de usuário e senha, como em um push normal. Informe-os e a partir disso você não precisará mais ter que informar novamente em seus próximos commits.

Caso não queira que essas informações fiquem permanentemente registradas na máquina, basta especificar um tempo de cache com o seguinte comando:

```
git config --global credential.helper 'cache --timeout 3600'
```

Lembrando que `--global` irá definir essa opção para todos os repositórios da máquina gerenciados pelo Git. Use `--local` para atribuir apenas no repositório em questão.

A opção de cache acima irá guardar seu login e senha por apenas 3600 segundos, ou seja, uma hora.

Em qualquer dúvida, basta deixar um comentário.
