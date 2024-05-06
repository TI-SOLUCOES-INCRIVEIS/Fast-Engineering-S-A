# Projeto de Migração para a AWS - Fast Engineering S/A
#### Este repositório contém a documentação do projeto final do Programa de Bolsas - AWS e DevSecOps | Compass UOL.
O projeto tem como objetivo aumentar a escalabilidade e reduzir custos operacionais com a migração para a AWS Cloud de um e-commerce.

#### Membros da Equipe:
- [Gustavo Pinheiro](https://github.com/Gustavopnhro)
- [Janaina Cordisco](https://github.com/JanainaACordisco)
- [Patrícia Moura](https://github.com/Tri3010)

### Caso
A "Fast Engineering S/A" está em busca de uma solução por parte da empresa terceira "T.I SOLUÇÕES INCRÍVEIS". O e-commerce da Fast Engineering S/A está experimentando um crescimento significativo e a solução atual não está mais conseguindo lidar com a alta demanda de acessos e compras que está enfrentando. Desde o início do ano, os acessos e as compras têm apresentado um aumento de 20% a cada mês.  
Neste contexto, a Fast Engineering S/A têm buscado formas de aumentar a disponibilidade, segurança, lidar com o aumento da demanda e reduzir custo com infraestrutura e gerenciamento de suas instalações do e-commerce. 

**Requerimentos do Pedido**
- Escopo.
- Arquitetura da Nova Solução.
- Valores.
- Prazo de Entrega.
- Cronograma Macro de Entregas.

Sobre a construção da arquitetura para o futuro website da empresa, é necessario seguir as melhores práticas DevOps.

**Requisitos da Nova Arquitetura**
- Ambiente Kubernetes.
- Banco de dados PaaS.
- MultiAZ.
- Segurança de backup de dados.
- Persistência dos dados.
- Balanceamento de carga com healthcheck.
- Segurança (liberar somente o necessário/mínimo acesso possível).

## Escopo do projeto
### **Arquitetura atual**

A empresa opera com uma infraestrutura composta por três servidores principais: um para banco de dados MySQL (armazenando dados da aplicação React), outro para execução da aplicação React e um terceiro para o servidor web, que também armazena e entrega os arquivos estáticos.

Embora funcional para a operação básica da aplicação, recomenda-se aprimorar aspectos como segurança, monitoramento, alta disponibilidade e automação, visando garantir o crescimento sustentável, a escalabilidade e o desempenho da plataforma.

![Arquitetura_Atual](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20atual.png)

### **Arquitetura da solução proposta**

Quando planejamos a implantação na AWS, podemos nos beneficiar com a adoção de serviços gerenciados que reduzem o esforço de tarefas operacionais que não agregam valor à estrutura da empresa, e nos permitem focar em melhorias dos serviços prestados aos clientes. Dessa forma, precisamos investir menos esforço para manter a infraestrutura e mais em entregar novas funcionalidades, garantindo que a aplicação se comporte de acordo com a expectativa dos usuários finais.

![PROJECT_ARCHITECTURE](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Arquitetura%20final.png)

### **Serviços Utilizados**

#### Amazon Route 53 
O Amazon Route 53 é um serviço DNS que permite registrar e gerenciar domínios, com roteamento de tráfego para recursos AWS, como ELB e CloudFront. Facilita o roteamento de tráfego eficiente e garante alta disponibilidade, direcionando acessos para instâncias e serviços AWS.  
- Uso: A requisição do cliente é enviada para o Amazon Route 53, que direciona o tráfego para o CloudFront apropriado com base no tipo de conteúdo solicitado (conteúdo estático, frontend ou API).

#### Amazon CloudFront  
O Amazon CloudFront é um serviço de Content Delivery Network (CDN) oferecido pela AWS. Sua principal função é acelerar a entrega de conteúdo estático e dinâmico, como páginas web, imagens, vídeos, scripts e outros arquivos multimídia aos usuários finais com baixa latência e alta disponibilidade.  
- Uso: Se o conteúdo solicitado for estático (imagens, CSS, JavaScript), o CloudFront o recupera do S3 e o entrega diretamente ao cliente com baixa latência e alta disponibilidade.  
    Se o conteúdo solicitado for o frontend da aplicação web, o CloudFront o recupera do S3 e o entrega ao navegador do cliente.  
    Se o conteúdo solicitado for uma API, o CloudFront o direciona para o Application Load Balancer.

#### Amazon Simple Storage Service
O Amazon S3 utiliza Buckets para armazenar e distribuir conteúdo estático, incluindo imagens, vídeos e arquivos, integrando-se ao CloudFront para uma entrega eficiente. Oferece armazenamento seguro e escalável para imagens, vídeos e arquivos.
- Uso: Armazenamento dos arquivos estáticos e de frontend da aplicação.

#### AWS WAF
O AWS Web Application Firewall é um serviço de firewall projetado para proteger aplicações web contra ataques comuns, proporcionando proteção avançada contra ameaças, garantindo a segurança de aplicativos da web.
- Uso: O WAF oferece uma ampla gama de recursos de segurança, como filtragem de IP, regras de bloqueio de URL e proteção contra DDoS. Ele é posicionado antes do Application Load Balancer, assim filtra o tráfego malicioso antes que chegue aos clusters do EKS.  
Essa configuração oferece a melhor proteção para sua aplicação web com o mínimo de impacto no desempenho e na complexidade.

#### Amazon VPC
O Virtual Private Cloud isola a infraestrutura na nuvem e fornece controle granular sobre a rede, criando uma rede privada virtual. Cria uma rede VPC, melhorando o controle de tráfego e a segurança da infraestrutura.
- Uso: Cria um ambiente de rede isolado e seguro na AWS, permitindo o controle granular do tráfego de rede e a segmentação de recursos. A VPC é dividida em sub-redes públicas e privadas, segregando recursos sensíveis (como bancos de dados) da internet pública.

#### Amazon ALB
Application Load Balancer é um serviço que distribui o tráfego entre várias instâncias ou recursos para garantir a alta disponibilidade e a escalabilidade de aplicativos.  
- Uso: O Application Load Balancer distribui o tráfego entre os clusters do EKS que executam o backend da aplicação web.

#### Amazon EKS
O Elastic Kubernetes Service atua como a base da arquitetura, oferecendo orquestração de contêineres por meio do Kubernetes. Proporciona orquestração de contêineres escalável, permitindo a expansão dinâmica e alta disponibilidade da aplicação.
- Uso: O EKS é responsável pelo gerenciamento do ciclo de vida dos conteinêres, incluindo provisionamento, escalonamento e reinicialização em caso de falhas.

#### Amazon Fargate
O Amazon Fargate é um serviço de computação sem servidor da AWS projetado para executar contêineres. Ele permite que você execute aplicativos em contêineres sem precisar provisionar e gerenciar servidores, o que significa que você não precisa se preocupar com a infraestrutura subjacente.
- Uso: Os conteinêres do Fargate executam o backend da aplicação web e se comunicam com o banco de dados RDS MySQL para recuperar ou armazenar dados e retornam as respostas ao cliente.

#### Amazon RDS MySQL 
O Amazon RDS é um serviço de banco de dados relacional oferecido pela AWS. Ele foi projetado para simplificar a administração, operação e escalabilidade de bancos de dados relacionais, permitindo que os desenvolvedores se concentrem em suas aplicações sem se preocupar com a gestão do banco de dados subjacente.
- Uso: O banco de dados RDS MySQL armazena os dados da aplicação web, como produtos, pedidos, usuários e informações de pagamento.

#### NAT Gateway
Um gateway NAT é um serviço de Network Address Translation (NAT – Conversão de endereços de rede). Você pode usar um gateway NAT para que as instâncias em uma sub-rede privada possam se conectar a serviços fora da VPC, mas os serviços externos não podem iniciar uma conexão com essas instâncias.
- Uso: O NAT Gateway permite que os conteinêres do Fargate nas sub-redes privadas se comuniquem com a internet e com outros serviços da AWS de forma segura.

#### Network ACL
A Network Access Control List é uma lista com camadas adicionais de segurança que controlam o tráfego de entrada e saída de sub-redes em sua VPC.
- Uso: Recurso de segurança que permite controlar o tráfego de entrada e saída das sub-redes dentro da VPC. 

#### AWS IAM
O AWS Identity and Access Management é um serviço que ajuda você a controlar o acesso aos recursos da AWS de forma segura. Com o IAM, é possível gerenciar, de maneira centralizada, permissões que controlam quais recursos da AWS os usuários poderão acessar. Você usa o IAM para controlar quem é autenticado (fez login) e autorizado (tem permissões) a usar os recursos.
- Uso: A IAM Role dentro do Fargate assume um papel crucial na atribuição de permissões e no controle de acesso para os conteinêres em execução. Ela funciona como uma identidade digital para os conteinêres, permitindo que eles acessem recursos específicos da AWS e realizem tarefas necessárias para a sua operação, como por exemplo permitindo a conexão com o banco de dados RDS.

#### Amazon CloudWatch
O Amazon CloudWatch é um serviço de monitoramento dos recursos da AWS e as aplicações executadas na AWS em tempo real. Você pode usar o CloudWatch para coletar e monitorar métricas, que são as variáveis que é possível medir para avaliar seus recursos e suas aplicações.
- Uso: Monitora a infraestrutura e a aplicação, fornecendo insights sobre desempenho, segurança e eventos, permitindo a prevenção, detecção e resolução rápida de problemas.

#### AWS Database Migration Service
O AWS DMS é um serviço de replicação e migração gerenciado que ajuda a mover workloads analíticos e bancos de dados para a AWS rapidamente, de forma segura e com o mínimo possível de inatividade e zero perda de dados.
- Uso: Permite migrar os dados do banco de dados on-premises para a AWS.


### Migração dos dados

Propomos a migração segura e eficiente do servidor MySQL on-premises para o Amazon RDS na nuvem utilizando o AWS Database Migration Service (DMS). O DMS garante replicação contínua dos dados durante a migração, assegurando integridade e consistência. 
O DMS facilita o processo com uma interface amigável para configuração e gerenciamento, além de oferecer monitoramento completo da migração. Com o AWS DMS e o RDS, garantimos uma migração tranquila, segura e eficiente para a nuvem e ao mesmo tempo, será possível desfrutar de escalabilidade sob demanda, confiabilidade e segurança robusta, redução de custos e alto desempenho. 

### Implementação

Na fase de implementação da arquitetura na AWS, utilizaremos uma abordagem de Integração Contínua e Implantação Contínua (CI/CD) para otimizar o desenvolvimento e a entrega.

Isso é essencial para a adoção das práticas DevOps, que visam a colaboração e a automação entre equipes de desenvolvimento e operações.

Nessa abordagem, integramos os seguintes serviços da AWS, que desempenham papéis fundamentais em automatizar o ciclo de vida de desenvolvimento, construção e implantação de aplicações:

- AWS CodeCommit
- AWS CodeBuild
- AWS CodeDeploy
- AWS CodePipeline

**AWS CodeCommit:** É um serviço de hospedagem de repositórios de controle de versão privados. Ele fornece um ambiente seguro e escalável para armazenar e gerenciar código-fonte. Com recursos de controle de acesso baseados em IAM, permite colaborações de maneira eficiente, controle de versões e rastreio de alterações ao longo do tempo.

**AWS CodeBuild:** É um serviço de compilação gerenciada que automatiza a construção, teste e geração de artefatos de código-fonte. Ele oferece ambientes de compilação sob demanda e escaláveis, permitindo criação e testes do código em paralelo. Tem suporte a vários ambientes de execução, podendo criar e empacotar aplicações para várias plataformas e arquiteturas.

**AWS CodeDeploy:** Serviço que automatiza a implantação de aplicativos em ambientes de teste e produção de forma consistente e controlada. Ele suporta implantações em instâncias EC2, serviços ECS e até mesmo ambientes on-premises. Com a automação de implantação, permite reduzir erros manuais e garante uma implantação uniforme em ambientes diferentes.

**AWS CodePipeline:** É um serviço de automação de CI/CD que cria fluxos automatizados para desenvolver, testar, implantar e entregar aplicações. Ele reage automaticamente a mudanças de código no repositório CodeCommit, permitindo entregas frequentes e confiáveis. Isso otimiza o processo de desenvolvimento e implantação.


### AWS Well-Architected Framework

A arquitetura proposta segue as melhores práticas e está de acordo com os pilares da AWS Well-Architected Framework.
         
![Pilares Well-Architected](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Pilares%20do%20AWS%20Well-Architected.png)
  
**Excelência Operacional** 

- A distribuição de recursos em várias zonas de disponibilidade aumenta a resiliência e a disponibilidade do sistema. 

- O uso de métricas e alarmes no Amazon CloudWatch permite monitorar continuamente a saúde e o desempenho do sistema, facilitando a identificação e correção de problemas operacionais. 

**Segurança**

- A configuração do AWS WAF protege contra ataques comuns da web, como injeções SQL, cross-site scripting (XSS) e DDoS. 

- A segregação de sub-redes públicas e privadas, juntamente com a configuração adequada de grupos de segurança e ACLs de rede, ajuda a garantir que os recursos estejam protegidos contra acesso não autorizado.  

**Confiabilidade** 

- As instâncias do EKS são distribuídas em várias zonas de disponibilidade dentro da mesma região da AWS, garantindo que a aplicação permaneça disponível em caso de falhas em uma zona.

- Amazon RDS Multi-AZ: O banco de dados RDS é replicado automaticamente para uma zona de disponibilidade secundária, garantindo a alta disponibilidade e recuperação rápida em caso de falha do banco de dados primário. 

- Os health checks do Application Load Balancer garantem que apenas instâncias saudáveis recebam tráfego.

- O uso de múltiplos NAT Gateways distribuídos em várias zonas de disponibilidade aumenta a resiliência do sistema, garantindo que o tráfego de saída continue fluindo mesmo em caso de falha em uma zona. 
 
**Eficiência de Desempenho**

- O uso do Amazon CloudFront para distribuir conteúdo estático e otimizar a entrega de frontend e APIs melhora o desempenho do sistema, reduzindo assim a latência e melhorando a experiência do usuário. 

- O Application Load Balancer distribui o tráfego de forma inteligente entre várias instâncias do Amazon EKS, garantindo alta disponibilidade e desempenho.

**Custo Otimizado** 

- Uso eficiente de recursos: O dimensionamento automático e a escolha de tipos de serviços adequados garantem que você utilize apenas os recursos que precisa, otimizando os custos da AWS.

- Monitoramento de custos: O CloudWatch pode ser utilizado para monitorar os custos da infraestrutura e identificar oportunidades de otimização.
  
**Sustentabilidade**

- Eficiência energética: O Fargate é uma plataforma serverless que utiliza apenas recursos computacionais necessários para executar os conteinêres, reduzindo o consumo de energia.

- Práticas sustentáveis: A AWS oferece diversas práticas sustentáveis para reduzir o impacto ambiental da infraestrutura, como a utilização de fontes renováveis de energia e a otimização da refrigeração de data centers.
 
## Valores

![Custo infraestrutura](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Custo%20arquitetura.png)
[Ver mais detalhes](https://calculator.aws/#/estimate?id=b01cde4e21b48acb8d9d7e39c42694d0838c1934)

### Custos

|             Item             |                        Descrição                        |     Preço     |
|:----------------------------:|:-------------------------------------------------------:|:-------------:|
| Migração de dados para a AWS | Migração de dados on-premises para a AWS.                |    $108,77    |
| Mão de obra                  | Custo da equipe de projeto e implementação.              |   $6.153,08   |
| Infraestrutura da AWS        | Custo mensal da infraestrutura de serviços da AWS.       |    $998,39    |
| Treinamento                  | Treinamento da equipe da Fast Engineering S/A.           |    $170,91    |
| Suporte                      | Suporte mensal pós-implementação (10 horas/mês).         |    $355,02    |
| **Custo único**              | **Total de custo único de implementação e treinamento.** | **$6.432,76** |
| **Custo mensal**             | **Total de custo mensal de infraestrutura e suporte.**   | **$1.353,41** |

## Cronograma Macro e Prazo de Entrega
- Prazo total de entrega: 24 dias úteis.

![Cronograma](https://github.com/TI-SOLUCOES-INCRIVEIS/Fast-Engineering-S-A/blob/main/assets/Cronograma%20Macro.png)
