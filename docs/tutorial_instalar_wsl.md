# Guia de Configuração do WSL no Windows

Este guia descreve o processo para habilitar e configurar o Windows Subsystem for Linux (WSL) no Windows, incluindo a validação do ambiente e os passos necessários para sua ativação.

---

## **1. Validação da Configuração do WSL**

1. Abra o terminal do Windows (PowerShell ou CMD).

2. Verifique se o WSL está configurado no sistema:
   ```bash
   wsl --list --verbose
   ```

* Se o WSL estiver configurado corretamente, será exibida uma lista de distribuições instaladas e suas respectivas versões.

* Caso apareça a mensagem abaixo, significa que o WSL não está habilitado:

```csharp
Este aplicativo requer o Subsistema do Windows para Linux Opcional.
Instale-o executando: wsl.exe --install --no-distribution
Talvez seja necessário reiniciar o sistema para que as alterações entrem em vigor.
Código de erro: Wsl/WSL_E_WSL_OPTIONAL_COMPONENT_REQUIRED
```

---

## **2. Habilitação do WSL**

1. No terminal do Windows (PowerShell) aberto como administrador, execute o seguinte comando para habilitar o WSL:
    ```bash
    wsl --install
    ```

2. Este comando:
    * Habilita o recurso opcional do WSL no Windows.
    * Configura o WSL 2 como versão padrão.
    * Baixa e instala automaticamente a distribuição padrão (Ubuntu).

3. Ao final do processo, pode ser necessário reiniciar o sistema para aplicar as alterações:
    * Certifique-se de salvar seu trabalho antes de reiniciar o computador.

---

## **3. Verificação da Instalação**

1. Após a reinicialização, abra novamente o terminal.

2. Verifique as distribuições instaladas e suas versões:

    ```bash
    wsl --list --verbose
    ```

    * A saída deve exibir a distribuição padrão instalada (por exemplo, Ubuntu) e a versão do WSL (1 ou 2).

3. Para confirmar que o WSL 2 está configurado como padrão, execute:

    ```bash
    wsl --set-default-version 2
    ```

---

## **4. Atualização e Gerenciamento de Distribuições**

1. Para listar todas as distribuições disponíveis para instalação:

    ```bash
    wsl --list --online
    ```

2. Para instalar uma nova distribuição:

    ```bash
    wsl --install -d <nome-da-distro>
    ```
    
    * Substitua `<nome-da-distro>` pelo nome da distribuição desejada.