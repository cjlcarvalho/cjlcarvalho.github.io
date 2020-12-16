---
title: "Tutorial – Instalando e configurando o Python e o Pip no Windows"
date: "2016-03-22"
---

**1\. Instale o Python**

O processo de instalação do Python no Windows começa através do download do instalador no seguinte endereço: [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Esse arquivo de instalação já vem com o IDLE integrado.

**2\. Configure as variáveis de ambiente**

Para configurar as variáveis de ambiente, clique no botão Iniciar. Logo em seguida pesquise por "variáveis de ambiente" na caixa de pesquisa. A opção "Editar variáveis de ambiente para a sua conta" será listada. Clique nela.

Após isso uma janela irá abrir. Nela é possível ver a caixa "Variáveis de usuário" e logo abaixo a caixa "Variáveis do sistema". Selecione a variável Path em "Variáveis do sistema" e clique em "Editar".

Escreva o seguinte no fim da coluna "Valor":

`;C:\PythonXX\;C:\PythonXX\Scripts`

Onde o "XX" será substituído por dois números referentes à versão do Python que está instalada em seu computador.

**3\. Download do Setup Tools e do Pip**

O Pip e o Setup Tools são gerenciadores de pacotes importantes para o interpretador Python. Faça os downloads deles nos seguintes links:

Setup Tools: [https://bootstrap.pypa.io/ez\_setup.py](https://bootstrap.pypa.io/ez_setup.py)

Pip: [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py)

Com o prompt de comando, acesse a pasta de downloads do seu sistema, como nos comandos a seguir:

`cd C:\Users\Usuario\Downloads`

`python get-pip.py`

`python ez_setup.py`

Com isso, os seus gerenciadores de pacotes estão devidamente instalados. Confira se o Pip está funcionando corretamente através do comando:

`pip --version`

Caso a mensagem "**erro:** **'pip' não é reconhecido como um comando interno ou externo, um programa operável ou um arquivo em lotes"** aparecer, acesse a pasta C:\\PythonXX\\Scripts através do prompt e digite:

`easy_install.exe pip`

`pip.exe install virtualenv`

Digite "pip --version" novamente e você verá que o erro parou de ocorrer e agora você pode utilizá-lo normalmente e baixar os seus pacotes necessários.
