# Arquitetura da demonstração e evolução prevista

## Prova de conceito publicada

A versão pública é uma aplicação estática autocontida. Essa decisão favorece avaliação imediata, portabilidade e preservação.

```mermaid
flowchart LR
    A["Registros demonstrativos"] --> B["Estado e filtros no navegador"]
    B --> C["Mapa territorial"]
    B --> D["Percurso organismo–bioativo–ensaio"]
    B --> E["Tabela acessível"]
    B --> F["Exportação CSV"]
```

Não há servidor de aplicação, autenticação, rastreamento ou transmissão de consultas. Dados, estilos, scripts e imagens demonstrativas estão incorporados em `index.html`.

## Arquitetura científica prevista

A infraestrutura completa separará responsabilidades que a prova de conceito reúne em um único arquivo:

```mermaid
flowchart LR
    A["Literatura e bases especializadas"] --> B["Busca reproduzível"]
    B --> C["Triagem e extração independente"]
    C --> D["Reconciliação taxonômica e territorial"]
    D --> E["Revisão humana identificada"]
    E --> F["Coleção de evidências verificadas"]
    F --> G["Consulta territorial"]
    F --> H["Exportações e pacote de replicação"]
    F --> I["Atlas de cobertura e lacunas"]
```

Cada resultado deverá manter a relação entre procedência, organismo, material, preparação ou biomolécula, ensaio, desfecho, passagem de sustentação e fonte. Identificadores reconhecidos apoiarão a ligação com recursos taxonômicos, químicos, proteicos e bibliográficos.

## Controles de qualidade

- protocolo de elegibilidade versionado;
- dupla extração em corpus de referência;
- concordância e erro relatados por campo;
- atribuição amazônica condicionada à procedência explícita do material;
- histórico de transformações e decisões curatoriais;
- distinção entre informação ausente, restrita e em revisão;
- testes funcionais, de acessibilidade, restauração e segurança;
- atualização documentada e depósitos persistentes.

## Acessibilidade e desempenho

Mapa e tabela oferecem percursos equivalentes. A interface implementa foco visível, navegação por teclado, regiões semânticas, mensagens para tecnologias assistivas, contraste em temas claro e escuro e redução de movimento conforme a preferência do sistema. O uso de aplicação estática também reduz o volume de transferência e o tempo de carregamento após o primeiro acesso.
