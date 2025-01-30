# Criar-um-script-para-alternar-versoes-no-Git-Bash
Script git bash mudar versao java

 
```bash
nano ~/set-java.sh
```

1. Adicione este conteúdo atualizado:


```bash
#!/bin/bash

# Caminho base onde estão os JDKs
JAVA_BASE="/e/Java"

# Verifica se um argumento foi passado
if [ -z "$1" ]; then
  echo "Uso: set-java 11, 17 ou 21"
  exit 1
fi

# Verifica se a versão existe
if [ -d "$JAVA_BASE/jdk-$1" ]; then
  export JAVA_HOME="$JAVA_BASE/jdk-$1"
  export PATH="$JAVA_HOME/bin:$PATH"
  echo "Java configurado para $(java -version 2>&1 | head -n 1)"
else
  echo "Erro: JDK $1 não encontrado em $JAVA_BASE"
  exit 1
fi

```

Salve (CTRL + X, depois Y e Enter).

Agora, torne o script executável:


```bash
chmod +x ~/set-java.sh
```

2. Adicionar um alias para facilitar o uso

Edite o arquivo ~/.bashrc para adicionar um alias para o script:

```bash
nano ~/.bashrc

```

Adicione esta linha no final:

```bash
alias set-java="source ~/set-java.sh"

```

Salve e recarregue:

```bash
source ~/.bashrc

```

3. Como usar

Agora, para alternar entre as versões do Java, use:

```bash
set-java 11   # Para usar o JDK 11
set-java 17   # Para usar o JDK 17
set-java 21   # Para usar o JDK 21


```

E para verificar a versão atual do Java:


```bash
java -version
```








