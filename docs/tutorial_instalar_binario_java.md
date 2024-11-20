# Guia de Instalação do Java 17 no Windows

Este documento contém o passo a passo para instalação e configuração do Java 17 no Windows.

---

## **1. Download do Binário do Java 17**

1. Acesse o site oficial da Oracle: [https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html).
2. Baixe a versão desejada do JDK 17 para Windows:
   - Escolha o arquivo [`Windows x64 Compressed Archive`](https://download.oracle.com/java/17/archive/jdk-17.0.12_windows-x64_bin.zip) para evitar instaladores.

---

## **2. Extração dos Arquivos**

1. Extraia o conteúdo do arquivo baixado para um local de sua escolha:
   - Por exemplo: `C:\binarios\java\jdk-17.0.12`.

---

## **3. Configuração de Variáveis de Ambiente**

1. **Adicionar o caminho do JDK ao `PATH`:**
   - Abra o menu **Iniciar** e procure por **Editar as variáveis de ambiente do sistema**.
   - Clique em **Variáveis de Ambiente**.
   - Localize a variável `Path` em **Variáveis do sistema** e clique em **Editar**.
   - Adicione o caminho `C:\binarios\java\jdk-17.0.12\bin` à lista.

2. **Criar a variável `JAVA_HOME`:**
   - No mesmo painel de variáveis de ambiente, clique em **Novo** em **Variáveis do sistema**.
   - Nome: `JAVA_HOME`
   - Valor: `C:\binarios\java\jdk-17.0.12`

3. **Configurar a variável `Path` para usar `JAVA_HOME`:**
   - Substitua o caminho do JDK na variável `Path` por `%JAVA_HOME%\bin`.

---

## **4. Verificação da Instalação**

1. Abra o terminal (PowerShell ou CMD) e digite:
   ```bash
   java -version
   ```

2. Saída esperada:
    ```code
    java version "17.x.x"
    Java(TM) SE Runtime Environment (build 17.x.x)
    Java HotSpot(TM) 64-Bit Server VM (build x.x.x, mixed mode)
    ```
Observação: Caso esteja aberto o terminal e tente validar que o java está configurado "java -version" a atualização feita em painel de variáveis não estará refletido, então precisará abrir um novo terminal para fazer a validação.
