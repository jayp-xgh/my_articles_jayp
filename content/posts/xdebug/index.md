---
title: "Xdebug, Docker, VsCode & Direnv"
date: 2024-03-21T20:00:19-03:00
draft: false
---

## Bora configurar o Xdebug

{{< default "span__name_date" >}}
  @jayp | Março 21, 2024
{{< /default >}}

![Postgres vs Mongo](/img/xdebug.webp)

> Nunca vi um tutorial simples ensinando a configurar o Xdebug com Docker e Direnv. Neste mini tutorial, vou tentar dar o meu máximo para esclarecer e ensiná-los. Lembrando que este não é um tutorial para explicar o que é o Xdebug ou como utilizá-lo, mas sim para instalá-lo. Para isso, você pode ler a [documentação](https://xdebug.org/docs/) ou assistir a este vídeo do [**YouTube**](https://www.youtube.com/watch?v=pi8-_hEIWJc).


Nesse tutorial utilizo:
- [x] [**PHP 7.3**](https://www.php.net/releases/7_3_0.php)
- [x] [**Docker**](https://docker-docs.uclv.cu/)
- [x] [**Zsh**](https://ohmyz.sh/)
- [x] [**Direnv**](https://direnv.net/docs/installation.html)

### Primeiro, vamos configurar o [**direnv**](https://direnv.net/).

Instalação:

```bash

    sudo apt install direnv
   
```
Para configurar o terminal, adicione a linha abaixo ao arquivo **.zshrc**. Assim, sempre que você acessar uma pasta contendo um arquivo **.envrc**, o Direnv será ativado automaticamente.

```bash

    eval "$(direnv hook zsh)"
   
```

Agora, vamos criar o arquivo .envrc com o seguinte conteúdo na raiz do seu projeto:

{{< warning "warning" >}}
    <strong>Alerta:</strong> Com essa implementação, o comando <strong><a href="https://man7.org/linux/man-pages/man1/hostname.1.html">hostname</a></strong> sempre retornará o IP mais recente do seu computador.
{{< /warning >}}

```bash

    #!/usr/bin/env bash

    export DOCKER_HOST_IP=$(hostname -I | awk '{print $1}')
   
```
> Na primeira vez que você acessar a pasta pelo terminal, será necessário executar o comando abaixo para permitir que o Direnv leia o arquivo **.envrc**

```bash

    direnv allow
   
```

No seu arquivo **Dockerfile**, é necessário habilitar o Xdebug, lembrando que o Xdebug é um **módulo** do PHP, então ele fica dentro do seu **php.ini**

```dockerfile

    # Instalar e habilitar extensões PECL e Xdebug
    RUN pecl install  -o -f xdebug-3.1.5 \
    && docker-php-ext-enable  xdebug
   
```

Ainda no **Dockerfile**, precisamos configurar o **php.ini**. Não vamos entrar manualmente no container para alterá-lo.

{{< warning "warning" >}}
    <strong>Alerta:</strong>Lembre-se de colocar o caminho correto do **php.ini** localizado dentro do container. No exemplo, estou usando o php-custom.ini que está no seguinte caminho:
{{< /warning >}}

```dockerfile

    COPY ./docker/php.ini /usr/local/etc/php/conf.d/php-custom.ini
   
```

Na raiz do seu projeto, crie uma pasta chamada docker e dentro dela um arquivo **php.ini**, Adicione a seguinte linha ao arquivo:

```ini

    xdebug.mode = develop,debug
   
```

> Neste exemplo, estou usando o PHP 7.3, o que implica que o Xdebug está na versão 3.1.5. Para verificar as versões compatíveis com o PHP, acesse este [**link**](https://xdebug.org/docs/compat).

No **docker-compose.yml**, adicione um bloco [**environment**](https://docs.docker.com/compose/environment-variables/set-environment-variables/) dentro do serviço do seu container que contenha o PHP.

```yml
    
    environment:
    - XDEBUG_CONFIG=client_host=${DOCKER_HOST_IP:-}
    
```
> Essa configuração define o endereço IP do cliente para o Xdebug no ambiente Docker. Nesse caso, o cliente é a sua máquina de desenvolvimento.


### Configurando a extensão do VsCode:

Instale a extensão que permitirá a depuração do código: [**PHP Debug**](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)

Após a instalação, abra o arquivo **launch.json**, apague todo o conteúdo e deixe apenas o seguinte script:

{{< warning "warning" >}}
    <strong>Alerta:</strong> O pathMappings é o local onde está o seu projeto dentro do container.
{{< /warning >}}

```json

    {
        "version": "0.2.0",
        "configurations": [
            {
                "name": "Listen for Xdebug",
                "type": "php",
                "request": "launch",
                "port": 9003,
                "pathMappings": {
                    "/var/www/html": "${pathMappings}"
                }
            }
        ]
    }
   
```

Para rodar começar a utilizar o Xdebug, coloque o **breakpoint** no local que deseja que o código pare, de preferencia para testar, coloque ele em um arquivo de conexão com o banco de dados, só para teste, deps rretire e coloque aonde desejar. Agora  basta apertar no play locazilado em algum lugar do seu vscode com a opção "Listen For Debug¨ ou *ctrl + shift + p*, e pesquise por **Debug (PHP) Start Listening for Xdebug**.

Agora vamos inicializar na web, em sua URL basta passar o seguinte parametro:

```bash

    ?XDEBUG_SESSION_START=true
   
```

vai ficar algo como: [http://127.0.0.1/dashboard?XDEBUG_SESSION_START=true](http://127.0.0.1/dashboard?XDEBUG_SESSION_START=true)

Após iniciar a sessão, não precisa mais passar esse parametro até que a sessão seja encerrada.
