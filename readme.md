# Autenticação Stateful e Stateless em Microserviços

## Indice
- [Autenticação Stateful e Stateless em Microserviços](#autenticação-stateful-e-stateless-em-microserviços)
  - [Indice](#indice)
  - [Descrição](#descrição)
  - [Autenticação Stateful x Stateless](#autenticação-stateful-x-stateless)
      - [Autenticação Stateless](#autenticação-stateless)
          - [Vantagens:](#vantagens)
          - [Desvantagens:](#desvantagens)
      - [Atenticação Stateful](#atenticação-stateful)
          - [Vantagens:](#vantagens-1)
          - [Desvantagens:](#desvantagens-1)

## Descrição
Este projeto contem uma estrutura simples de microserviços para fins didaticos sobre os conceitos e aplicações de applicações web com autenticação stateful e stateless.

## Autenticação Stateful x Stateless
> [!NOTE]
> Stateful e Stateless são termos abrangentes que podem ser aplicados a diferentes funcionalidades de uma aplicação, o escopo deste projeto esta na aplicação destes conceitos a autenticação e autorização de web apis, informações na integra podem ser encontrados em [Stateful vs. stateless](https://www.redhat.com/en/topics/cloud-native-apps/stateful-vs-stateless).

#### Autenticação Stateless
Um método muito utilizado na autenticação stateless é o [JWT (Jason Web Token)](https://jwt.io/introduction), podem ser enviadas dados pertinentes a autenticação atraves do payload, em posse da chave privada, a mensagem pode ser decriptada e validada.

###### Vantagens:
- Maior performace: Não é necessario realizar uma requisição para validar o token no serviço de autenticação, toda vez que o cliente fizer uma requisição para utilizar uma funcionalidade da api alvo.

###### Desvantagens:
- Dificuldade para controlar acesso as funcionalidades: após a autenticação do usuario, não é possivel bloquear seu acesso ate o tempo de expiração do token. (Existem formas de bloquear o acesso atraves de block lists, porem neste caso estamos saindo do um cenário stateless, pois será necessario armazenar os tokens bloqueados).

#### Atenticação Stateful
O metodo de autenticação stateful possui uma forma proprietaria de token, ou seja, cada applicação pode possuir uma implementação diferente, mas geralmente são um id no formato UUID para identificação da seção armazenada (Em um banco de dados, ou em memória por exemplo) e obtenção dos dados da seção e usuario.

###### Vantagens:
- Maior Controle sobre a seção do usuario: é possivel revogar o acesso de determinado token para bloquear ou deslogar um usuario

###### Desvantagens:
- Overload do serviço de autenticação: O serviço de autenticação pode ser sobrecarregado com diversas chamadas, pois para todas as requisições feitas pelos clients será necessario realizar um verficicação do token.


