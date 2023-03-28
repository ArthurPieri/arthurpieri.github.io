---
title: "WSL2 and VSCode"
author: "Arthur Pieri"
tags: 
- 
---
# Por quê?

O Windows Sybsystem for Linux permite aos desenvolvedores rodar um ambiente GNU/Linux – incluindo a maioria das ferramentas de linhas de comando, utilities e aplicações – diretamente no windows, sem o custo geralmente associado a Máquiinas virtuais tradicionais ou DualBoot.

O WSL cria um espaço onde você pode instalar diferentes versões do Linux e integrar algumas ferramentas para facilitar o desenvolvimento em diferentes plataformas.

Dentro da Área de dados vamos utilizar várias ferramenta de código aberto da Apache Foundation, porém algumas das ferramentas utilizadas funcionam apenas no Linux. por isso é importante ter disponível tal ambiente.

# Instalando o WSL2

Para instalar o WSL2 vamos utilizar o [tutorial disponibilizado pela própria Microsoft](https://docs.microsoft.com/pt-br/windows/wsl/install).

## Pré-requisitos

Você deve estar executando o Windows 10 versão 2004 e superior (Build 19041 e superior) ou o Windows 11.

## Instalando

1.  Abrir o Windows Powershell como Administrador e execute

2. Após o fim da instalação execute

3. Para executar a linha de comando, procure por: Ubuntu

## (Opcional) Executar o script para configuração básica do sistema

O script a seguir foi feito para criar um setup inicial no seu ambiente Ubuntu

1.  Acesse: [http://github.com/ArthurPieri/Scripts/blob/master/terraforming.sh](http://github.com/ArthurPieri/Scripts/blob/master/terraforming.sh)
2.  Copie todo o script
3.  Abra seu terminal Linux e digite

4. Copie todo o conteudo do script para o terminal (para colar o que foi copiado você pode usar o botão direito do mouse)

5. ‘ctrl+x’ para fechar e 'y' para confirmar

6. Transforme o arquivo em um executável com o comando:

7. Execute o arquivo

8. Siga as instruções que apareceram na sua tela

### Github e Chaves SSH

1.  Para copiar a chave SSH para o GITHUB e facilitar o download dos repositórios, primeiro pegue as informações da sua chave pública

2. Copie a chave que aparece:

3. Acesse: [https://github.com/settings/keys](https://github.com/settings/keys)

4. Selecione a opção: “add new SSH key” ou “Adicionar nova chave SSH”

![](http://localhost:2368/content/images/2022/01/image-11.png)

5. Cole a informação que você copiou no campo: Key

![](http://localhost:2368/content/images/2022/01/image-12.png)

6. No campo Title coloque um nome que seja significativo e te ajude a lembrar a qual máquina essa chave pertence

7. Finalize clicando em “Add SSH Key”

# Instalando o VScode

1.  Para instalar o VSCode basta ir até o site: [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
2.  Buscar a versão do seu sistema operacional
3.  Baixar o arquivo
4.  Instalar o arquivo.

# Configurando o VScode para integrar com o WSL2

1.  Após a instalação do VSCode
2.  Na barra iniciar, procure por vscode
3.  execute
4.  Para fazer a integração com o WSL2 vá em extensions e procure por ‘Remote’ e instale as extensões:
5.  Remote - WSL
6.  Remote - Development

![](http://localhost:2368/content/images/2022/01/image-13.png)

5. Após o fim da instalação, para acessar seu ambiente Linux, vá até o canto inferior esquerdo e clique no quadrado verde e selecione a opção: NEW WSL WINDOW

![](http://localhost:2368/content/images/2022/01/image-14.png)

6. O vscode vai abrir uma nova janela, instalar as ferramentas necessárias no seu ambiente linux.

7. Você pode confirmar que a Janela que você está utilizando está conectada ao WSL olhando na parte inferior esquerda do VSCode deve apresentar: WSL: Ubuntu

![](http://localhost:2368/content/images/2022/01/image-15.png)

# Finalizando

Dessa forma você agora consegue executar códigos e ferramentas do Linux diretamente nessa Janela do VSCode.