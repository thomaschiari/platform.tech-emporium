# Structure

## Diagrama de Funcionamento de Serviços

Aqui está descrito como é o funcionamento de nossa aplicação, com os serviços e suas interações.

![Diagrama de Funcionamento de Serviços](img/Screenshot%20from%202024-06-01%2001-42-02.png)

Os nossos serviços são interligados e se comunicam entre si para fornecer uma experiência completa ao usuário. O Gateway é responsável por redirecionar as requisições para os serviços apropriados, enquanto os serviços de autenticação, contas, produtos e pedidos gerenciam as operações específicas de cada área. O serviço de pagamentos, implementado posteriormente, também é integrado ao sistema para permitir transações seguras e eficientes.

## Diagrama de Funcionamento de Infraestrutura

![Diagrama de Funcionamento de Infraestrutura](img/Screenshot%20from%202024-06-01%2001-42-40.png)

A infraestrutura do Tech Emporium é composta por diversos componentes que garantem o funcionamento adequado dos serviços. O Redis é utilizado como cache de alta performance em todo o sistema, enquanto o Discovery Service é responsável por localizar os microsserviços. O Tech Emporium DB é o banco de dados central que armazena todas as informações persistentes, e o Circuit Breaker garante a resiliência dos serviços em caso de falhas, utilizando a biblioteca Resilience4j.

```mermaid
classDiagram
    class Gateway {
        +Redireciona requisições
    }
    class AuthService {
        +Gerencia autenticação
        +AuthResource
    }
    class AccountService {
        +Gerencia contas de usuário
        +AccountResource
    }
    class ProductService {
        +Gerencia produtos
        +ProductResource
    }
    class OrderService {
        +Gerencia pedidos
        +OrderResource
    }

    Gateway --> AuthService : Redireciona autenticação
    Gateway --> AccountService : Redireciona gerenciamento de contas
    Gateway --> ProductService : Redireciona gerenciamento de produtos
    Gateway --> OrderService : Redireciona gerenciamento de pedidos

    AuthService ..> AuthResource : Utiliza
    AccountService ..> AccountResource : Utiliza
    ProductService ..> ProductResource : Utiliza
    OrderService ..> OrderResource : Utiliza
```

```mermaid
classDiagram
    class Redis {
        +Cache de alta performance
    }
    class DiscoveryService {
        +Serviço de descoberta
    }
    class TechEmporiumDB {
        +Banco de dados central
    }
    class CircuitBreaker {
        +Mecanismo de resiliência
    }

    DiscoveryService --|> AuthService
    DiscoveryService --|> AccountService
    DiscoveryService --|> ProductService
    DiscoveryService --|> OrderService

    Redis --|> AuthService
    Redis --|> ProductService
    Redis --|> OrderService

    TechEmporiumDB --|> AuthService
    TechEmporiumDB --|> AccountService
    TechEmporiumDB --|> ProductService
    TechEmporiumDB --|> OrderService

    CircuitBreaker --|> AuthService
    CircuitBreaker --|> AccountService
    CircuitBreaker --|> ProductService
    CircuitBreaker --|> OrderService
```