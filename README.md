# Tech Emporium
Repositório de Documentação e Referências de microsserviços para o projeto Tech Emporium de Plataformas, APIs e Microsserviços

### Alunos:
- [Lucca Hiratsuca Costa](https://github.com/LuccaHiratsuca)
- [Thomas Chiari Ciocchetti de Souza](https://github.com/thomaschiari)

### Descrição Geral:
Tech-Emporium simula uma loja online de produtos de tecnologia, em que usuários podem se autenticar, e usuários autenticados podem cadastrar produtos, alterar produtos, criar orders, alterar orders e deletar orders. 

### Serviços: 
- Account

Link para repositório: [Account](https://github.com/LuccaHiratsuca/platform.store.account)

- Account Resource

Link para repositório: [Account Resource](https://github.com/LuccaHiratsuca/platform.store.account-resource)

- Auth

Link para repositório: [Auth](https://github.com/LuccaHiratsuca/platform.store.auth)

- Auth Resource

Link para repositório: [Auth Resource](https://github.com/LuccaHiratsuca/platform.store.auth-resource)

- Gateway

Link para repositório: [Gateway](https://github.com/LuccaHiratsuca/platform.store.gateway)

- Discovery

Link para repositório: [Discovery](https://github.com/LuccaHiratsuca/platform.store.discovery)

- Product

Link para repositório: [Product](https://github.com/thomaschiari/platform.tech-emporium.products)

- Product Resource

Link para repositório: [Product Resource](https://github.com/thomaschiari/platform.tech-emporium.product-resource)

- Order

Link para repositório: [Order](https://github.com/thomaschiari/platform.tech-emporium.orders)

- Order Resource

Link para repositório: [Order Resource](https://github.com/thomaschiari/platform.tech-emporium.order-resource)

- Docker API

Link para repositório: [Docker API](https://github.com/LuccaHiratsuca/platform.store.docker-api)

- Tech Emporium DB

Link para repositório: [Tech Emporium DB](https://github.com/thomaschiari/platform.tech-emporium.db)

- Redis

Link para repositório: [Redis](https://github.com/LuccaHiratsuca/platform.tech-emporium.redis)


```mermaid
graph TD;
    style Usuario fill:#f9f,stroke:#333,stroke-width:2px;
    style Gateway fill:#bbf,stroke:#333,stroke-width:2px;
    style AccountService fill:#bbf,stroke:#333,stroke-width:2px;
    style AuthService fill:#bbf,stroke:#333,stroke-width:2px;
    style ProductService fill:#bbf,stroke:#333,stroke-width:2px;
    style OrderService fill:#bbf,stroke:#333,stroke-width:2px;
    style AccountResource fill:#dfd,stroke:#333,stroke-width:2px;
    style AuthResource fill:#dfd,stroke:#333,stroke-width:2px;
    style ProductResource fill:#dfd,stroke:#333,stroke-width:2px;
    style OrderResource fill:#dfd,stroke:#333,stroke-width:2px;
    style Redis fill:#f66,stroke:#333,stroke-width:2px;
    style DiscoveryService fill:#ff9,stroke:#333,stroke-width:2px;
    style TechEmporiumDB fill:#ccf,stroke:#333,stroke-width:2px;
    style CircuitBreaker fill:#cfc,stroke:#333,stroke-width:2px;

    Usuario[Usuário] --> Gateway;
    Gateway --> AccountService[Account Service];
    Gateway --> AuthService[Auth Service];
    Gateway --> ProductService[Product Service];
    Gateway --> OrderService[Order Service];
    
    AccountService --> AccountResource[Account Resource];
    AuthService --> AuthResource[Auth Resource];
    ProductService --> ProductResource[Product Resource];
    OrderService --> OrderResource[Order Resource];
    
    AuthService --> Redis;
    ProductService --> Redis;
    OrderService --> Redis;

    DiscoveryService[Discovery Service] --> AccountService;
    DiscoveryService --> AuthService;
    DiscoveryService --> ProductService;
    DiscoveryService --> OrderService;
    
    AccountService --> TechEmporiumDB;
    AuthService --> TechEmporiumDB;
    ProductService --> TechEmporiumDB;
    OrderService --> TechEmporiumDB;
    
    CircuitBreaker[Circuit Breaker] --> AccountService;
    CircuitBreaker --> AuthService;
    CircuitBreaker --> ProductService;
    CircuitBreaker --> OrderService;
