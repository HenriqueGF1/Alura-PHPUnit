Um teste sempre segue um estrutura padrão, que tem três partes

(Given-When-Then)
Dado-Quando-(then)Então 

A parte dado descreve o estado do mundo antes de você iniciar o comportamento que está especificando neste cenário. Você pode pensar nisso como as pré-condições para o teste.
A seção quando é o comportamento que você está especificando.
Finalmente, a seção then descreve as mudanças que você espera devido ao comportamento especificado.

A inicialização do cenário (Arrange ou Given)
(inserindo os dados)
A execução da regra de negócio (Act ou When)
(retornando os dados atraves da regra de negocio)
A verificação do resultado (Assert ou Then)
(verificar se os resultados combinam com os resultados esperados na regra de negocio)

Exemplo

Recurso: usuário negocia ações
  Cenário: O usuário solicita uma venda antes do fechamento da negociação
    Dado que tenho 100 ações da MSFT
       E eu tenho 150 ações da APPL
       E a hora é antes do fechamento da negociação

    Quando peço para vender 20 ações da MSFT
     
     Então eu deveria ter 80 ações da MSFT
      E eu deveria ter 150 ações da APPL
      E uma ordem de venda de 20 ações da MSFT deveria ter sido executada

Suporte
https://martinfowler.com/bliki/GivenWhenThen.html

Executar 

./vendor/bin/phpunit --colors tests

Classes de Equivalência

Sobre classes de equivalência do mundo de testes, que descrevem similaridades entre os cenários de testes
Isto é importante para descobrir quantos testes devemos criar
A ideia é criar nenhum teste a mais ou a menos