# Como configurar/instalar/usar o `docker` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar/usar o `docker` no `Linux Ubuntu`.

## _Abstract_

_This document contains the main commands and settings for configuring/installing/using the `docker` on `Linux Ubuntu`._


## Descrição [2]

### `docker`

`Docker` é uma plataforma de código aberto que simplifica o processo de criação, implantação e execução de aplicativos em contêineres. Os contêineres permitem empacotar um aplicativo juntamente com suas dependências em uma unidade isolada, garantindo que ele seja executado de maneira consistente em qualquer ambiente. Com o `Docker`, os desenvolvedores podem criar ambientes de desenvolvimento replicáveis, implementar aplicativos de forma rápida e eficiente, e dimensionar facilmente aplicativos em ambientes de produção. Ele oferece uma maneira flexível e leve de encapsular aplicativos, facilitando a distribuição e a escalabilidade.


## 1. Como configurar/instalar/usar o `docker` no `Linux Ubuntu` [1][3]

Para configurar/instalar/usar o `docker` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update`

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes: `sudo apt --fix-broken install`

    2.6 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`
    

Para instalar o `Docker` no `Linux Ubuntu 22.04 LTS` através do `Terminal Emulator`, você pode seguir os passos abaixo. Esse processo instala a versão mais recente do `Docker Engine` disponível para `Ubuntu 22.04`.

1. **Instale os pacotes necessários para permitir que o `apt` use um repositório sobre HTTPS:** 

    ```
    sudo apt install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release -y
    ```
2. **Adicione a chave GPG oficial do `Docker`:**  `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

3. **Use o comando a seguir para configurar o repositório do `Docker`:**

    ```
    echo \
        "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

4. **Atualize o índice de pacotes do `apt` novamente:** `sudo apt update -y`

5. **Instale o `Docker Engine`, CLI do `Docker`, e `Containerd`:** `sudo apt install docker-ce docker-ce-cli containerd.io -y`

6. **Para garantir que o `Docker` seja iniciado automaticamente na inicialização do sistema, execute:** `sudo systemctl enable docker`

7. **Para verificar se o `Docker` foi instalado corretamente e está funcionando, rode:** `sudo docker run hello-world`

    Este comando baixa uma imagem de teste e executa um container utilizando essa imagem. Se o container rodar com sucesso, isso indica que a instalação do `Docker` foi bem-sucedida.

**Nota Importante:**

- **Executar o `Docker` como usuário não-`root`:** Por padrão, o comando `Docker` precisa ser executado com `sudo`. Para executar o `Docker` como um usuário não-`root`, você precisa adicionar seu usuário ao grupo `docker` com o comando: `sudo usermod -aG docker $USER`

    Após isso, faça logout e login novamente para que as alterações tenham efeito.

Siga esses passos para instalar o Docker no `Ubuntu 22.04 LTS` usando o `Terminal Emulator`.

### 1.1 Código completo para configurar/instalar/usar

Para configurar/instalar/usar o `docker` no `Linux Ubuntu` sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abra o terminal. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Digite o seguinte comando e pressione `Enter`:

    ```
    sudo apt clean                                                            
    sudo apt autoclean
    sudo apt autoremove -y
    sudo apt update
    sudo apt --fix-broken install
    sudo apt clean
    sudo apt list --upgradable
    sudo apt full-upgrade -y
    sudo apt install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release -y
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    echo \
        "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    sudo apt update -y
    sudo apt install docker-ce docker-ce-cli containerd.io -y
    sudo systemctl enable docker
    sudo docker run hello-world
    sudo usermod -aG docker $USER
    ```


## Referências

[1] OPENAI. ***Instale Docker no Ubuntu.*** Disponível em: <https://chat.openai.com/c/96806087-1b85-4f30-96b4-88a2a0f00f1a> (texto adaptado). Acessado em: 05/04/2023 17:11.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 05/04/2024 17:10.

