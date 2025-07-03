# 📦 O que é Docker?
Docker é uma plataforma open source que permite ao desenvolvedor empacotar sua aplicação em ambientes portáteis e isolados, chamados containers. Isso garante que o projeto possa ser executado em qualquer lugar, independentemente do sistema operacional ou configurações da máquina local.

## ✅ Vantagens
Isolamento e segurança: o Docker executa a aplicação em um ambiente isolado chamado container, evitando conflitos com o sistema host.

Execução simultânea: é possível executar diversos containers simultaneamente em uma mesma máquina.

Centralização: pacotes, código e ambiente de execução são agrupados em uma única imagem.

Integração com CI/CD: o Docker facilita a automação de testes, builds e deploys em pipelines.

## 💡 Cenário de uso
Imagine o seguinte fluxo:

Os desenvolvedores escrevem código localmente e compartilham seu trabalho usando containers Docker.

Eles utilizam Docker para enviar os aplicativos para um ambiente de testes (automatizados e manuais).

Quando um bug é encontrado, ele pode ser corrigido localmente e reimplantado para revalidação.

Finalizados os testes, o deploy para produção pode ser feito facilmente, enviando a imagem atualizada ao ambiente produtivo.

## 🧱 Imagem
Uma imagem Docker é um conjunto de instruções para criar um container.

É possível criar uma imagem a partir de outra imagem base, customizando apenas o necessário para sua aplicação.

Para criar uma imagem Docker, defina um arquivo Dockerfile na raiz do projeto com os comandos necessários.

Obs: Ao modificar o Dockerfile e reconstruir a imagem, apenas as camadas alteradas são recompiladas, otimizando o processo.

## 📦 Container
Um container é uma instância executável de uma imagem.

É possível criar, iniciar, parar, excluir e inspecionar containers via linha de comando (CLI) ou através da API do Docker.
