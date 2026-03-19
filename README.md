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

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: 
    ```bash
    sudo apt update -y
    ```

    2.5 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:
    
    ```bash
    sudo apt list --upgradable
    ```

    2.6 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update -y`. Digite o seguinte comando e pressione `Enter`:
    
    ```bash
    sudo apt full-upgrade -y
    ```

    2.7 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    
    ```bash
    sudo apt autoremove -y
    ```

    2.8 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    
    ```bash
    sudo apt autoclean
    ```

3. **Você poderá instalar o `yt-dlp` usando o comando**:Use versão _standalone_ (melhor que `pip` e `apt`):

    ```bash
    sudo rm -f /usr/bin/yt-dlp

    sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp \
    -o /usr/local/bin/yt-dlp

    sudo chmod a+rx /usr/local/bin/yt-dlp
    ```

4. Verificar a versão:

    ```bash
    yt-dlp --version
    ```

5. Depois de concluir a instalação do `yt-dlp`, você pode usar o comando `yt-dlp` para baixar vídeos do `YouTube` como demonstrado anteriormente: 
    
    ```bash
    yt-dlp https://www.youtube.com/watch?v=VxnHJkpl4oo
    ```

    - Isso deve permitir que você baixe vídeos do YouTube com sucesso.


## 2. Configurar `alias`

1. **Cria um `alias` no `.zshrc`**:

    ```bash
    alias ytmp4='yt-dlp -f "bv*+ba/b" --merge-output-format mp4'
    alias ytmp3='yt-dlp -x --audio-format mp3'
    ```

2. **Usar**:

    ```bash
    ytmp4 URL
    ytmp3 URL
    ```

## 3. Comandos

### 3.1 Pesquisar e baixar vídeos no `YouTube`

1. Acessar o `YouTube`;

2. Encontrar o vídeo que deseja baixar;

3. Copiar URL do vídeo;

4.  **Para pesquisar e baixar o vídeo do `YouTube`**: Se você deseja buscar vídeos no `YouTube` usando uma pesquisa, você deve usar a opção `ytsearch` seguida do termo de pesquisa. Por exemplo, se você deseja buscar e baixar vídeos sobre `"FreeCAD Tutorial"`, você pode usar o comando:

    ```bash
    yt-dlp "ytsearch:FreeCAD Tutorial"
    ```

    Isso irá pesquisar o `YouTube` e baixar o primeiro vídeo encontrado relacionado ao termo de pesquisa.

### 3.2 Baixar _playlist_ organizada por pastas

1. Cada _playlist_ vira uma pasta, e os vídeos ficam numerados:

    ```bash
    yt-dlp -f bestvideo+bestaudio \
    -o "~/Downloads/%(playlist_title)s/%(playlist_index)s - %(title)s.%(ext)s" \
    https://www.youtube.com/playlist?list=ID_DA_PLAYLIST
    ```

    Resultado:

    ```bash
    Downloads/
    └── Nome da Playlist/
        ├── 01 - Video A.mp4
        ├── 02 - Video B.mp4
    ```


### 3.3 Baixar só áudio (MP3)

1. Ideal para aulas, _podcasts_ etc.:

    ```bash
    yt-dlp -x --audio-format mp3 \
    -o "~/Downloads/%(title)s.%(ext)s" \
    URL
    ```

    Se quiser qualidade máxima:

    ```bash
    --audio-quality 0
    ```


### 3.4 Forçar saída em MP4 (mais compatível)

1. Evita `.webm` (que às vezes dá problema no `VLC`):

    ```bash
    yt-dlp -f "bv*+ba/b" --merge-output-format mp4 URL
    ```

### 3.5 Baixar só um trecho do vídeo

1. Muito útil:

    ```bash
    yt-dlp --download-sections "*00:05:00-00:10:00" URL
    ```

    Baixa só de 5 min até 10 min.



### 3.6 Baixar apenas alguns vídeos da _playlist_

1. Exemplo: só os 5 primeiros:

    ```bash
    yt-dlp --playlist-items 1-5 URL_DA_PLAYLIST
    ```



### 3.7 Continuar _downloads_ interrompidos

1. **Continuar _downloads_ interrompidos**:

    ```bash
    yt-dlp -c URL
    ```



### 3.87Melhor configuração "completa" (recomendada)

1. Essa aqui é praticamente sua versão final:

    ```bash
    yt-dlp \
        -f "bv*+ba/b" \
        --merge-output-format mp4 \
        --embed-metadata \
        --embed-thumbnail \
        --add-metadata \
        --concurrent-fragments 5 \
        -o "~/Downloads/%(playlist_title)s/%(playlist_index)s - %(title)s.%(ext)s" \
        URL
    ```

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
    sudo rm -f /usr/bin/yt-dlp

    sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp \
        -o /usr/local/bin/yt-dlp

    sudo chmod a+rx /usr/local/bin/yt-dlp
    yt-dlp --version
    ```

## Referências

[1] OPENAI. **Instalar o `yt-dlp` no `linux ubuntu` pelo `terminal emulator`.** Disponível em: <https://chat.openai.com/c/87f54416-69e5-448d-a8c4-b65b7d4ba0ad> (texto adaptado). ChatGPT. Acessado em: 04/10/2023 21:29.

[2] OPENAI. **Vs code: editor popular.** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 27/01/2025 14:25.
