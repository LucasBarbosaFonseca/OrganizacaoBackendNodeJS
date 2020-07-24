# Organização e Padronização do código Backend em Node.js

Em nossos projetos devemos adotar padrões de organização de código, organizando cada coisa em seu lugar, 
deixando as rotas da aplicação apenas com as responsabilidades de receber requisição, repassar os dados 
da requisição a outro arquivo e devolver resposta. Além de tudo isso escrito anteriormente também é estudado e
implementado nesse pequeno projeto o Typescript.
Aqui escrevi de forma resumida, mas nesse link está escrito sobre organizações e patterns:

[Repository, service e patterns](https://www.notion.so/Repository-service-e-patterns-82419cceb11c4c4fbbc055ade7fb1ac5)

# O que está sendo estudado nesse pequeno projeto
Nesse pequeno projeto foi estudado e implementado além de Typescript, os conceitos de Model,
Repository, Service e alguns patterns do SOLID. Abaixo estão os detalhes de alguns conceitos estudados.

#### Model

Para começar isolar um pouco a aplicação vamos aplicar o Model que é como se fosse uma entidade, um modelo cujo sua 
responsabilidade é declarar os formatos dos dados que vamos armazenar no banco de dados por exemplo.

#### Repository

O Repository é um arquivo que irá servir como um ponte que liga nossa aplicação com o banco de dados. 
A responsabilidade do Repository é ter toda a forma, todas as funções que comunicamos com os dados no 
banco de dados, fazendo as operações como create, read, update, delete. O Repository é um detentor de operações de banco de dados. 

#### Service

O Service é um arquivo que sua responsabilidade é tratar toda a regra de negócio de uma operação específica como por exemplo 
a criação de reservas de hotel, que dentro dessa operação há outras ações encadeadas nessa operação principal sendo regras 
de negócio verificar disponibilidade de quartos, efetuar pagamento e  fazer envio de email. 
Um arquivo service é responsável por uma operação, a de cadastro por exemplo. O arquivo deve ter um nome descritivo como 
createAppointmentHotel.ts. Cada arquivo service tem uma única e exclusiva função com um nome padrão execute que irá ter 
toda a regra de negócio de um cadastro de reserva de hotel por exemplo.


## Por que tudo isso?
Os Services e Repositories são utilizados para construir uma base sólida, visando a escabilidade e aplicação de boas práticas. 
Com o seu uso, apesar de uma maior complexidade no ínicio, é possível obter diversos benefícios ao atender princípios 
importantes da programação. Alguns deles são:

- **SoC (Separation of Concerns)**: 
Esse princípio zela pela separação de responsabilidades de cada arquivo. Exemplo: as rotas não devem ser responsáveis por lidar 
com a persistência dos dados, isso fica por conta do Repository. Já o Repository não é responsável pela tratativa das regras de negócio, 
isso é responsabilidade dos Services;

- **DRY (Don't Repeat Yourself)**:
Esse princípio zela pelo maior reaproveitamento de código. Esse princípio não preza necessariamente pela não-repetição de 
código e sim regras de negócio. Exemplo: ao criar Services e Repositories, você possibilita a reutilização desses códigos no restante da aplicação;

- **SRP (Single Responsability Principle)**:
Esse princípio zela que uma classe deve possuir apenas uma responsabilidade. Exemplo: Ao criar um service chamado createTransactionService, 
devemos garantir que no seu único método (execute()) seu trabalho seja apenas a criação de uma transação;

- **DIP (Dependency Inversion Principle)**:
Esse princípio zela que uma entidade dependa apenas de abstrações, não de implementações. Exemplo: Ao atribuir ao Repository a comunicação 
com o Banco de dados, o Service precisa interagir apenas com essa abstração, sem precisar criar uma nova instância e realizar as ações diretamente;


## Onde entra o SOLID?

O SOLID é uma sigla que representa 5 princípios da programação orientada a objetos:

- **SRP (Single Responsability Principle)**;
- **OCP (Open–closed Principle)**;
- **LSP (Liskov substitution Principle)**;
- **ISP (Interface segregation Principle)**;
- **DIP (Dependency Inversion Principle)**.

E ele entra justamente nessa abordagem que estamos utilizando (Repositories e Services). Os princípios **DIP** e **SRP** provavelmente 
são os mais fáceis de enxergar nesse primeiro momento, mas ao longo dos meus estudos o **SOLID** será aplicado cada vez mais, 
conforme entendemos mais o funcionamento do Typescript e nos acostumamos com o Data Mapper Pattern.

Quer ler mais sobre SOLID, confira [esse outro documento](https://www.notion.so/Princ-pios-do-SOLID-d469618bbd2049668eaf80e889194cce) com exemplos de código.
