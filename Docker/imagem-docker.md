## 🚀 Trabalhando com imagens e containers em Docker

Esta sessão trataremos de como é formado uma estrutura de uma imagem Docker e as diferenças entre imagens e containers, além de comandos importantes.


---

1. Qual é a diferença entre imagens e contêineres do Docker?

Uma imagem Docker é um template que contém todos os componentes necessários para que a sua aplicação seja executada (código, bibliotecas, frameworks, build do sistema operacional e etc).
A imagem Docker é consumida assim que um contêiner é iniciado.

Há duas formas de utilizar uma imagem Docker, criando-a do zero, dessa forma, você define todos os componentes que estarão na sua imagem e consumidas pelo contêiner ou podemos baixar uma imagem pronta (o que é mais comum) e fazer apenas modificações que sejam necessárias para a nossa aplicação.
Para baixar uma imagem, você pode acessar o Docker Hub (hub.docker.com/) aonde se encontram repositórios disponíveis tanto pelos fabricantes do softwares quanto por usuários.
