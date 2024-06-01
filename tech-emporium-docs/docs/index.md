# Tech Emporium Documentation

Bem-vindo à documentação do Tech Emporium! Este projeto simula uma loja online de produtos de tecnologia, construída utilizando microsserviços e APIs.

## Estrutura do Projeto

### Serviços
O projeto é composto por diversos serviços implementados em Java usando Spring Boot:

- **Account**: Gerencia as contas de usuário.
- **Account Resource**: API de recursos de contas.
- **Auth**: Gerencia autenticação e autorização.
- **Auth Resource**: API de recursos de autenticação.
- **Product**: Gerencia os produtos disponíveis na loja.
- **Product Resource**: API de recursos de produtos.
- **Order**: Gerencia os pedidos dos usuários.
- **Order Resource**: API de recursos de pedidos.
- **Gateway**: Redireciona as requisições para os serviços apropriados.
- **Discovery**: Serviço de descoberta para localizar os serviços.
- **Docker API**: Interface para gerenciar contêineres Docker.
- **Tech Emporium DB**: Banco de dados central.
- **Redis**: Cache de alta performance.
- **Paypal**: Integração com o serviço de pagamento Paypal.
- **Paypal Resource**: API de recursos de pagamento.

### Infraestrutura
A infraestrutura do projeto inclui os seguintes componentes:

- **Redis**: Utilizado para caching.
- **Discovery Service**: Serviço de descoberta para localização de microsserviços.
- **TechEmporiumDB**: Banco de dados centralizado para armazenar informações.
- **Circuit Breaker**: Mecanismo de resiliência usando Resilience4j.

### Estrutura
Aqui está uma imagem descritiva da estrutura de nosso projeto, com explicações.

![Diagrama de Estrutura](img/Diagrama%20Tech%20Emporium.png)

- O usuário acessa o **Gateway**, que redireciona as requisições para os serviços apropriados.
- O **Discovery Service** é utilizado para que os serviços se encontrem.
- O **Grafana** e o **Prometheus** monitoram a saúde dos serviços, providenciando observabilidade.

Mais informações podem ser encontradas na documentação de cada componente.

Explore a documentação para obter mais detalhes sobre cada componente e sua integração no projeto.

<script>
mermaid.initialize({ startOnLoad: true });
</script>
