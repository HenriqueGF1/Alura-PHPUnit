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

Data Providers!

Sobre Data Providers, os provedores de dados permitem que "alimentemos" os testes com cenários diversos, sem repetir o código e os asserts
Os data providers permitem rodar um mesmo teste inúmeras vezes de acordo com uma fonte de dados e passando argumentos diferentes em cada vez.
Deve-se criar um método sem o prefixo test para ser o dataProvider.
O método deve retornar um array multidimensional, ou seja, uma lista de valores utilizados para a realização dos testes.
O método de teste será executado uma vez para cada item do data provider, ou seja, se o data provider tiver três itens, o método de teste seja executado três vezes.
Métodos de testes não podem ter argumentos, com exceção para métodos que possuem um data provider.
O método que for utilizar o data provider deve utilizar a anotação @dataProvider getDataForTests.
Os valores de cada item serão informados como argumentos do método de testes.
Pode-se adiciona uma chave para identificar um item do data provider tornando mais fácil a identificação de um erro.

-- Métodos

A tarefa mais demorada ao escrever testes de unidade normalmente é preparar o cenário, utilizando os dados necessários para o teste, e depois desfazer as ações que possam afetar outros testes.

Para executar código antes ou depois de testes, o PHPUnit nos fornece as fixtures. São métodos que vão ser executados em momentos específicos.

public static function setUpBeforeClass(): void - Método executado uma vez só, antes de todos os testes da classe
public function setUp(): void - Método executado antes de cada teste da classe
public function tearDown(): void - Método executado após cada teste da classe
public static function tearDownAfterClass(): void - Método executado uma vez só, após todos os testes da classe


Que existe um método setUp, que é chamado antes de cada teste
Que os provedores de dados sempre são executados antes do método setup
Que caso queiramos executar algum código antes dos provedores de dados, existe o método setUpBeforeClass
Que, análogo ao setUp e setUpBeforeClass, existem os métodos tearDown e tearDownAfterClass, para executar um código após os testes

Como verificar que o código lança as exceções esperadas
Em geral, exceções também fazem parte das regras de negócio e precisam ser verificadas
Para tal o PHPUnit oferece os métodos expectException e expectExceptionMessage da classe TestCase:
expectException(\NomeDaExcecao::class)
expectExceptionMessage(mensagemDeExcecao)