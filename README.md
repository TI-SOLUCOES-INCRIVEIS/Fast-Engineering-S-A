# Projeto final - Cloud AWS
Documentação do projeto final do Programa de Bolsas - AWS e DevSecOps | Compass UOL

#### Membros da Equipe:
- [Gustavo Pinheiro](https://github.com/Gustavopnhro)
- [Janaina Cordisco](https://github.com/JanainaACordisco)
- [Patrícia Moura](https://github.com/Tri3010)

### Caso:
A "Fast Engineering S/A" está em busca de uma solução por parte da empresa terceira "TI SOLUÇÕES INCRÍVEIS". O eCommerce da Fast Engineering está experimentando um crescimento significativo e a solução atual não está mais conseguindo lidar com a alta demanda de acessos e compras que está enfrentando. Desde o início do ano, os acessos e as compras têm apresentado um aumento de 20% a cada mês.

**Arquitetura Atual**
* 01 servidor para Banco de Dados MySQL;
* 01 servidor para a aplicação utilizando REACT;
* 01 servidor de web Server e que armazena estáticos como fotos e links.

**Requerimentos do Pedido**
- Escopo.
- Arquitetura da Nova Solução.
- Valores.
- Prazo de Entrega.
- Cronograma Macro de Entregas.

Sobre a construção da arquitetura para o futuro website da nossa empresa, é necessario seguir as melhores práticas DevOps.

**Requesitos da Nova Arquitetura**
- Ambiente Kubernetes.
- Banco de dados PaaS.
- MultiAZ.
- Segurança de backup de dados.
- Persistência dos dados.
- Balanceamento de carga com healthcheck.
- Segurança (liberar somente o necessário/mínimo acesso possível).
  
Objetivo: Monte a proposta e a arquitetura do que a equipe propõe entregar.

___

## Projeto de Migração para a AWS - Fast Engineering S/A

## Introdução

Este repositório contém a documentação e o escopo do projeto de migração para a AWS de um e-commerce. O projeto tem como objetivo aumentar a escalabilidade e reduzir custos operacionais.

## Motivação do Cliente

A motivação por trás desta migração é a necessidade de atender à crescente demanda de acessos e compras que a Fast Engineering S/A está enfrentando.

## Escopo do Projeto

### Avaliação da Infraestrutura Atual.

![Arquitetura_Atual](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20atual.png)

### Arquitetura da Solução Proposta:

A arquitetura proposta segue as melhores práticas e está de acordo com os pilares da AWS Well-Architected Framework.
    
 ### Pilares da AWS Well-Architected Framework
      
![Pilares Well-Architected](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Pilares%20do%20AWS%20Well-Architected.png)
  
  ### Migração de Dados
  
A equipe está implementando uma migração de banco de dados crucial para o AWS RDS, adotando uma abordagem que prioriza a eficiência e a continuidade operacional. O AWS Database Migration Service (DMS) será utilizado para assegurar uma transição suave, replicando os dados de forma contínua e mantendo sua integridade. Essa estratégia tem como objetivo minimizar qualquer impacto nas operações diárias, ao mesmo tempo em que se aproveita os benefícios da escalabilidade e segurança oferecidos pela AWS. A equipe está comprometida em garantir que essa migração se concretize como uma transição tranquila e bem-sucedida.
  
  ### Serviços Utilizados

- **AWS Database Migration Service**
  - O AWS Database Migration Service facilita a migração de bancos de dados para a AWS com segurança e facilidade.

- **Amazon Route 53**
  - O Amazon Route 53 é um serviço DNS que permite registrar e gerenciar domínios, com roteamento de tráfego para recursos AWS, como ELB e CloudFront. Facilita o roteamento de tráfego eficiente e garante alta disponibilidade, direcionando acessos para instâncias e serviços AWS.

- **AWS Web Application Firewall (WAF)**
  - O AWS Web Application Firewall é um serviço de firewall projetado para proteger aplicações web contra ataques comuns, proporcionando proteção avançada contra ameaças, garantindo a segurança de aplicativos da web.
  
- **Amazon CloudFront**
  - O Amazon CloudFront é um serviço de Content Delivery Network (CDN) oferecido pela Amazon Web Services (AWS). Sua principal função é acelerar a entrega de conteúdo estático e dinâmico, como páginas web, imagens, vídeos, scripts e outros arquivos multimídia, aos usuários finais com baixa latência e alta disponibilidade.

- **Amazon Virtual Private Cloud (VPC)**
  - O Virtual Private Cloud isola a infraestrutura na nuvem e fornece controle granular sobre a rede, criando uma rede privada virtual. Cria uma rede VPC, melhorando o controle de tráfego e a segurança da infraestrutura.

 - **Application Load Balancer**
   - O Application Load Balancer é um serviço que distribui o tráfego entre várias instâncias ou recursos para garantir a alta disponibilidade e a escalabilidade de aplicativos. 

- **Amazon EKS**
  - O Elastic Kubernetes Service atua como a base da arquitetura, oferecendo orquestração de contêineres por meio do Kubernetes. Proporciona orquestração de contêineres escalável, permitindo a expansão dinâmica e alta disponibilidade da aplicação.

- **Amazon EC2**
  - O Amazon EC2 fornece instâncias virtuais sob demanda com configuração personalizável para uma ampla variedade de cargas de trabalho. Escalabilidade sob demanda, permitindo a adaptação rápida às necessidades de computação, sem investimentos antecipados em hardware físico.

- **Amazon RDS MySQL** 
  - O Amazon RDS (Relational Database Service) é um serviço de banco de dados relacional oferecido pela Amazon Web Services (AWS). Ele foi projetado para simplificar a administração, operação e escalabilidade de bancos de dados relacionais, permitindo que os desenvolvedores se concentrem em suas aplicações sem se preocupar com a gestão do banco de dados subjacente.

- **Amazon Simple Storage Service (S3)**
  - O Amazon S3 utiliza Buckets para armazenar e distribuir conteúdo estático, incluindo imagens, vídeos e arquivos, integrando-se ao CloudFront para uma entrega eficiente. Oferece armazenamento seguro e escalável para imagens, vídeos e arquivos.

- **Amazon CloudWatch**
  - O Amazon CloudWatch é um serviço de monitoramento e observação que fornece insights sobre o desempenho dos recursos e aplicativos AWS.
 
- **AWS Backup**
  - O AWS Backup é um serviço de backup totalmente gerenciado que ajuda a simplificar a proteção de dados e a recuperação de recursos da AWS.

- **AWS CodeBuild**
  - O AWS CodeBuild é um serviço de compilação totalmente gerenciado que compila código fonte, executa testes e cria artefatos.

- **AWS CodePipeline**
  - O AWS CodePipeline é um serviço de entrega contínua que automatiza a construção, teste e implantação de aplicativos.

- **AWS CodeDeploy**
  - O AWS CodeDeploy é um serviço de implantação automatizada que facilita a implantação de aplicativos na AWS.

- **CloudFormation**
  - O AWS CloudFormation é um serviço que permite criar e gerenciar recursos da AWS por meio de modelos de infraestrutura como código.

 
  **Nova Arquitetura**
  
![PROJECT_ARCHITECTURE](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20final.png)

### Valores

[Estimativa da Nova Arquitetura](https://calculator.aws/#/estimate?id=ac4b05484def49f1053d80b5c2167dfc62498e20)

**Custos**

|             Item                   |                     Descrição                      |       Preço      |
|------------------------------------|----------------------------------------------------|----------------  |
| Migração Para a AWS                | Migração de dados on-premise para a AWS            | $923,82          |
| Infraestrutura da AWS              | Custo da Infraestrutura de serviços da AWS         | $/Mensal |
| Custo da Equipe                    | Suporte e manutenção técnica                       | $/Mensal |

### Prazo de Entrega

+ Implementação da arquitetura: **28 dias úteis**.

Equipe de 3 pessoas:
  - Trabalhando 8 horas por dia
  - Ao longo de 28 dias úteis
  - Total de 672 horas para a entrega

### Cronograma Macro de Entregas

![Cronograma](https://github.com/zSalocin/PB_Compass_Projeto_Final_Arquitetura/blob/main/Assets/Cronograma.jpeg)
