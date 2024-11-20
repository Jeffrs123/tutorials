# Guia de Instalação do Docker no WSL

Este documento descreve o processo completo para instalar e configurar o Docker no Windows Subsystem for Linux (WSL).

---

## **1. Pré-requisitos**

1. Certifique-se de que o WSL está configurado e rodando no modo WSL 2.
   - Verifique a versão com:
     ``````bash
     wsl --list --verbose
     ```
   - Se necessário, configure sua distribuição para o WSL 2:
     ``````bash
     wsl --set-version <nome-da-distro> 2
     ```

2. Certifique-se de que o sistema Linux dentro do WSL está atualizado:
   ``````bash
   sudo apt update && sudo apt upgrade -y


---

## **2. Instalar os Pacotes Necessários**

1. Instale os pacotes requeridos para o Docker:

    ```bash
    sudo apt install -y ca-certificates curl gnupg lsb-release
    ```

2. Adicione a chave GPG oficial do Docker:

    ```bash
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```

3. Adicione o repositório do Docker:

    ```bash
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

4. Atualize a lista de pacotes:

    ```bash
    sudo apt update
    ```



---

## **3. Instalação do Docker**

1. Instale o Docker Engine e seus componentes:

    ```bash
    sudo apt install -y docker-ce docker-ce-cli containerd.io
    ```

2. Verifique se o serviço do Docker está funcionando:

    ```bash
    sudo service docker start
    ```

3. Execute o comando de teste:

    ```bash
    sudo docker run hello-world
    ```




---

## **4. Configuração de Permissões**

1. Crie o grupo docker (se ele não existir) e adicione seu usuário a ele:

    ```bash
    sudo groupadd docker
    sudo usermod -aG docker $USER
    ```

2. Reinicie o terminal do WSL:

    ```bash
    exit
    wsl
    ```

3. Teste o Docker sem usar sudo:

    ```bash
    docker ps
    ```

4. Caso ocorra erro de permissão, ajuste as permissões do socket:

    ```bash
    sudo chmod 666 /var/run/docker.sock
    ```




---

## **5. Configuração para Inicialização do Docker**

1. O Docker não inicia automaticamente por padrão no WSL. Para corrigir isso, você pode usar o seguinte comando para iniciar o serviço manualmente:

    ```bash
    sudo service docker start
    ```

    2. Alternativamente, configure o Docker para iniciar automaticamente ao abrir o WSL:

        * Edite o arquivo ~/.bashrc ou ~/.zshrc:
        ```bash
        nano ~/.bashrc
        ```

        * Adicione a linha:
        ```bash
        sudo service docker start
        ```

        * Salve e saia do editor.
        * Aplique as alterações:
        ```bash
        source ~/.bashrc
        ```




---

## **6. Testando o Docker**
1. Verifique se o Docker está funcionando corretamente:

    ```bash
    docker run hello-world
    ```

2. Liste os containers ativos (mesmo sem containers rodando, o comando deve funcionar):

    ```bash
    docker ps
    ```

3. Baixe e execute uma imagem de teste, como o Nginx:

    ```bash
    docker run -d -p 8080:80 nginx
    ```

    * Acesse no navegador: http://localhost:8080.



---

## **7. Solução de Problemas**

* Erro de permissão ao acessar o Docker socket:

    * Certifique-se de que o comando sudo chmod 666 /var/run/docker.sock foi executado.
    * Reinicie o terminal para aplicar as permissões.

* Erro ao iniciar o serviço Docker:

    * Verifique o status do serviço:
    ```bash
    sudo service docker status
    ```

    * Reinicie o serviço:
    ```bash
    sudo service docker restart
    ```




