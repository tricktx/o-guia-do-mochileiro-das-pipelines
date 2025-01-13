# O que é Docker?

Docker é uma plataforma open source que o desenvolvedor consegue empacotar toda a sua aplicação em ambientes portateis e dessa forma, conseguimos replicar todo o projeto, independente da instalação ou do sistema operacional do seu computador. 



#### - As vantagens: 
1. O Docker consegue empacotar e executar a sua aplicação em um ambiente chamado container, logo, um sinonimo de isolamento e segurança. 
2. Nesse processo, você consegue executar diversos containeres simultaneamente em um determinada hospedagem
3. Centralização de pacotes, códigos e ambientes.
4. Fácil integração em pipelines de CI/CD.

#### - Cenário: 
- Imagine o seguinte cenário: 
    1.Seus desenvolvedores escrevem código localmente e compartilham seu trabalho com seus colegas usando contêineres do Docker.
    2. Eles usam o Docker para enviar seus aplicativos para um ambiente de teste e executar testes automatizados e manuais.
    3. Quando os desenvolvedores encontram bugs, eles podem corrigi-los no ambiente de desenvolvimento e reimplantá-los no ambiente de teste para teste e validação.
    4. Quando o teste é concluído, levar a correção ao cliente é tão simples quanto enviar a imagem atualizada para o ambiente de produção.

---

#### - Imagem:

- Uma imagem Docker é uma "lista" de instruções para a criação de um Docker Container. Há a possibilidade de uma imagem ser criada a partir de outra imagem, com apenas algumas alterações e definições que se aplicam a a sua aplicação.
- Para você criar uma imagem Docker, cre um `Dockerfile` na raiz do seu projeto e defina comandos para construção da sua imagem e posteriomente, do seu Container.
- `Ps: Quando você altera o Dockerfile e há a reconstrução da imagem, apenas as camadas que foram alteradas serão reconstruídas, por esse motivo, ` 


#### - Container:

- Um Contêiner é uma instância executável de uma imagem.
- Há a possibilidade de criar, parar, excluir e outras ações no container através do CLI ou de uma API.
