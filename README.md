# Projeto de Migração para a AWS - Fast Engineering S/A
#### Este repositório contém a documentação do projeto final do Programa de Bolsas - AWS e DevSecOps | Compass UOL.
O projeto tem como objetivo aumentar a escalabilidade e reduzir custos operacionais com a migração para a AWS Cloud de um e-commerce.

#### Membros da Equipe:
- [Gustavo Pinheiro](https://github.com/Gustavopnhro)
- [Janaina Cordisco](https://github.com/JanainaACordisco)
- [Patrícia Moura](https://github.com/Tri3010)

### Caso:
A "Fast Engineering S/A" está em busca de uma solução por parte da empresa terceira "TI SOLUÇÕES INCRÍVEIS". O eCommerce da Fast Engineering está experimentando um crescimento significativo e a solução atual não está mais conseguindo lidar com a alta demanda de acessos e compras que está enfrentando. Desde o início do ano, os acessos e as compras têm apresentado um aumento de 20% a cada mês.  
Neste contexto, a Fast Engineering S/A têm buscado formas de aumentar a disponibilidade, segurança, lidar com o aumento da demanda e reduzir custo com infraestrutura e gerenciamento de suas instalações do eCommerce. 

**Requerimentos do Pedido**
- Escopo.
- Arquitetura da Nova Solução.
- Valores.
- Prazo de Entrega.
- Cronograma Macro de Entregas.

Sobre a construção da arquitetura para o futuro website da empresa, é necessario seguir as melhores práticas DevOps.

**Requesitos da Nova Arquitetura**
- Ambiente Kubernetes.
- Banco de dados PaaS.
- MultiAZ.
- Segurança de backup de dados.
- Persistência dos dados.
- Balanceamento de carga com healthcheck.
- Segurança (liberar somente o necessário/mínimo acesso possível).

## Escopo do projeto
### Arquitetura atual

A empresa opera com uma infraestrutura composta por três servidores principais: um para banco de dados MySQL (armazenando dados da aplicação React), outro para execução da aplicação React e um terceiro para servidor web, armazenamento e entrega de arquivos estáticos.

Embora funcional para a operação básica da aplicação, recomenda-se aprimorar aspectos como segurança, monitoramento, alta disponibilidade e automação, visando garantir o crescimento sustentável, a escalabilidade e o desempenho da plataforma.

![Arquitetura_Atual](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20atual.png)

### Arquitetura da solução proposta

Quando planejamos a implantação na AWS, podemos nos beneficiar com a adoção de serviços gerenciados que reduzem o esforço de tarefas operacionais que não agregam valor à estrutura da empresa, e nos permitem focar em melhorias dos serviços prestados aos clientes. Dessa forma, precisamos investir menos esforço para manter a infraestrutura e mais em entregar novas funcionalidades, garantindo que a aplicação se comporte de acordo com a expectativa dos usuários finais.

![PROJECT_ARCHITECTURE](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20final.png)

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




















### AWS Well-Architected Framework

A arquitetura proposta segue as melhores práticas e está de acordo com os pilares da AWS Well-Architected Framework.
         
![Pilares Well-Architected](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Pilares%20do%20AWS%20Well-Architected.png)
  
**Excelência Operacional:** 

- A distribuição de recursos em várias zonas de disponibilidade aumenta a resiliência e a disponibilidade do sistema. 

- O uso de métricas e alarmes no Amazon CloudWatch permite monitorar continuamente a saúde e o desempenho do sistema, facilitando a identificação e correção de problemas operacionais. 

**Segurança:**

- A configuração do AWS WAF protege contra ataques da web comuns, como injeções SQL e cross-site scripting (XSS). 

- A segregação de subnets públicas e privadas, juntamente com a configuração adequada de grupos de segurança e ACLs de rede, ajuda a garantir que os recursos estejam protegidos contra acesso não autorizado.  

**Confiabilidade:** 

- As instâncias do EKS são distribuídas em várias Availability Zones dentro da mesma região da AWS, garantindo que a aplicação permaneça disponível em caso de falhas em uma zona.

- Amazon RDS Multi-AZ: O banco de dados RDS é replicado automaticamente para uma Availability Zone secundária, garantindo a alta disponibilidade recuperação rápida em caso de falha do banco de dados primário. 

- O uso de múltiplos NAT Gateways distribuídos em várias zonas de disponibilidade aumenta a resiliência do sistema, garantindo que o tráfego de saída continue fluindo mesmo em caso de falha em uma zona. 
 
**Eficiência de Desempenho:**

- O uso do Amazon CloudFront para distribuir conteúdo estático e otimizar a entrega de frontend e APIs melhora o desempenho do sistema, reduzindo a latência e melhorando a experiência do usuário. 

- O Application Load Balancer o distribui o tráfego de forma inteligente entre várias instâncias do Amazon EKS, garantindo alta disponibilidade e desempenho.

- Distribuir tráfego de saída entre vários NAT Gateways e usar instâncias do Amazon RDS MySQL standby para backups e recuperação de desastres otimiza os custos operacionais e melhora a eficiência do sistema. 

**Custo Otimizado:** 

- Uso Eficiente de Recursos: O dimensionamento automático e a escolha de tipos de serviços adequados garantem que você utilize apenas os recursos que precisa, otimizando os custos da AWS.

- Monitoramento de Custos: O CloudWatch pode ser utilizado para monitorar os custos da infraestrutura e identificar oportunidades de otimização.
  
**Sustentabilidade:**

- Eficiência Energética: O Fargate é uma plataforma serverless que utiliza apenas os recursos computacionais necessários para executar os containers, reduzindo o consumo de energia.

- Práticas Sustentáveis: A AWS oferece diversas práticas sustentáveis para reduzir o impacto ambiental da infraestrutura, como a utilização de fontes renováveis de energia e a otimização da refrigeração de data centers.

















    
   # 
  ### Migração de Dados
  
A equipe está implementando uma migração de banco de dados crucial para o AWS RDS, adotando uma abordagem que prioriza a eficiência e a continuidade operacional. O AWS Database Migration Service (DMS) será utilizado para assegurar uma transição suave, replicando os dados de forma contínua e mantendo sua integridade. Essa estratégia tem como objetivo minimizar qualquer impacto nas operações diárias, ao mesmo tempo em que se aproveita os benefícios da escalabilidade e segurança oferecidos pela AWS. A equipe está comprometida em garantir que essa migração se concretize como uma transição tranquila e bem-sucedida.
  
 
 
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
