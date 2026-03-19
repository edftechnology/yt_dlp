# Como configurar/instalar o `yt-dlp` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar o Warsaw do `yt-dpl` no `Linux Ubuntu`.

## _Abstract_

_This document contains the main commands and configurations to configure/install Warsaw from `yt-dpl` on `Linux Ubuntu`._

## Descrição [2]

### `yt-dlp`

O `yt-dlp` é uma ferramenta de linha de comando escrita em `Python` que permite aos usuários baixar vídeos de inúmeros _sites_ de compartilhamento de vídeos como o `YouTube`, `Facebook`, `Vimeo` e muitos outros. É um `fork` do popular `youtube-dlc`, que por sua vez é uma continuação do `youtube-dl`, e traz melhorias significativas em termos de velocidade, funcionalidades e a capacidade de contornar as restrições de _download_ impostas por alguns _sites_. Com `yt-dlp`, você pode baixar vídeos em diferentes formatos e qualidades, extrair áudio, baixar _playlists_ inteiras, e até mesmo configurar _downloads_ automáticos através de _scripts_, fazendo dele uma ferramenta versátil e poderosa para armazenamento _offline_ de conteúdo de vídeo.


## 1. Configurar/Instalar o `yt-dlp` `Linux Ubuntu` [1]

Para configurar/instalar o `yt-dlp`, você pode seguir estas etapas:

1. Abra o terminal. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```


2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    ```bash
    sudo apt clean
    ```
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update -y`

    2.5 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.6 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update -y`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`

    2.7 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.8 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

3. **Você poderá instalar o `yt-dlp` usando o comando**:

    ```bash
    sudo apt install yt-dlp -y
    ```

4. Depois de concluir a instalação do `yt-dlp`, você pode usar o comando `yt-dlp` para baixar vídeos do `YouTube` como demonstrado anteriormente: 
    
    ```bash
    yt-dlp https://www.youtube.com/watch?v=VxnHJkpl4oo
    ```

    - Isso deve permitir que você baixe vídeos do YouTube com sucesso.


### 1.1 Alternativa para baixar vídeo

1. Tentar outra abordagem para baixar o vídeo. Tente baixar o vídeo utilizando um formato específico para ver se o problema é relacionado à seleção automática do formato. Você pode usar o seguinte comando:

    ```bash
    yt-dlp -f bestvideo+bestaudio https://www.youtube.com/watch?v=aPbRfDPQlNg
    ```

### 1.2 Atualizar o `yt-dlp`

Atualize o `yt-dlp` via `apt` (gerenciador de pacotes). Você pode tentar atualizar o `yt-dlp` diretamente via `apt` para garantir que você tenha a versão mais recente disponível nos repositórios do `Debian`:

1. **Remova o `yt-dlp` instalado via `apt`**:

    ```bash
    sudo apt remove yt-dlp -y
    ```

2. **Instale a versão mais recente diretamente do `pip`**: Primeiro, instale o `pip3` (caso ainda não tenha):

    ```bash
    sudo apt install python3-pip -y
    ```

3. **Em seguida, instale a versão mais recente do `yt-dlp`**:

    ```bash
    sudo pip3 install -U yt-dlp
    ```

Isso deve garantir que a versão mais recente do `yt-dlp` esteja instalada, o que pode ajudar a corrigir problemas com a extração de conteúdo do `YouTube`.



### 1.3 Pesquisar e baixar vídeos no YouTube

1. Acessar o `YouTube`;

2. Encontrar o vídeo que deseja baixar;

3. Copiar URL do vídeo;

4.  **Para pesquisar e baixar o vídeo do `YouTube`**: Se você deseja buscar vídeos no `YouTube` usando uma pesquisa, você deve usar a opção `ytsearch` seguida do termo de pesquisa. Por exemplo, se você deseja buscar e baixar vídeos sobre `"FreeCAD Tutorial"`, você pode usar o comando:

    ```bash
    yt-dlp "ytsearch:FreeCAD Tutorial"
    ```

    Isso irá pesquisar o `YouTube` e baixar o primeiro vídeo encontrado relacionado ao termo de pesquisa.

### 1.4 Baixar uma  _playlist_  inteira do `YouTube`

Para baixar uma _playlist_ inteira do YouTube usando o yt-dlp, basta seguir este passo a passo. O processo é bastante simples e você só precisa fornecer a URL da playlist.

1. **Obtenha o URL da Playlist**: Vá até a _playlist_ no YouTube e copie o link da playlist. A URL deve ser algo assim:

    ```bash
    https://www.youtube.com/playlist?list=ID_DA_PLAYLIST
    ```

2. **Baixar a Playlist**: Use o comando `yt-dlp` para baixar a playlist. O `yt-dlp` baixará todos os vídeos da _playlist_ de forma automática. Use o seguinte comando:

    ```bash
    yt-dlp -f bestvideo+bestaudio https://www.youtube.com/playlist?list=<ID_DA_PLAYLIST>
    ```

    Onde `<ID_DA_PLAYLIST>` é o `ID` da _playlist_ que você copiou do `YouTube`.

    O `-f bestvideo+bestaudio` especifica que o `yt-dlp` deve baixar a melhor qualidade de vídeo e áudio.

Caso prefira baixar todos os vídeos de uma vez sem selecionar formatos, você pode remover o parâmetro `-f bestvideo+bestaudio` e o `yt-dlp` irá escolher a melhor opção automaticamente.

## 2. Código completo para configurar/instalar

Para configurar/instalar o `yt-dlp`p no `Linux Ubuntu` sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt clean
    sudo apt autoclean
    sudo apt autoremove
    sudo apt update -y
    sudo apt autoremove
    sudo apt autoclean
    sudo apt list --upgradable
    sudo apt full-upgrade -y
    sudo apt install yt-dlp` -y
    ```

## Referências

[1] OPENAI. ***Baixar vídeos do youtube.*** Disponível em: <https://chat.openai.com/c/87f54416-69e5-448d-a8c4-b65b7d4ba0ad> (texto adaptado). ChatGPT. Acessado em: 04/10/2023 21:29.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 27/01/2025 14:25.
