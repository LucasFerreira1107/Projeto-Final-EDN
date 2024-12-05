# Projeto-Final-EDN
## Projeto final da Escola da Nuvem - Infraestrutura automatizada
![Automatização da Infraestrutura (1)](https://github.com/user-attachments/assets/f449d172-9d5d-444d-b6d1-d41913131af6)


# Componentes e Funções
## Amazon Route 53:

Serviço de gerenciamento de DNS que direciona usuários finais para o endpoint apropriado. É usado aqui para gerenciar o tráfego para a aplicação, garantindo alta disponibilidade.

## Amazon CloudFront:

Rede de distribuição de conteúdo (CDN) que entrega dados de forma rápida e segura aos usuários, armazenando em cache conteúdo estático em localizações geográficas próximas ao cliente. Trabalha em conjunto com o S3 para fornecer baixa latência.

## AWS Certificate Manager (ACM):

Gerencia certificados SSL/TLS, garantindo comunicação segura entre os usuários e os serviços na arquitetura.

## Amazon S3:

Armazena objetos estáticos, como imagens, vídeos ou arquivos de configuração. Ideal para servir conteúdo estático via CloudFront.
 ## Amazon EC2:

Máquinas virtuais que hospedam a aplicação. Estão configuradas em um grupo de auto scaling para escalabilidade e implementadas em sub-redes públicas em diferentes zonas de disponibilidade para garantir alta disponibilidade.

## Elastic Load Balancer (ELB):

Distribui automaticamente o tráfego de entrada entre as instâncias EC2 em diferentes zonas de disponibilidade, garantindo balanceamento de carga e tolerância a falhas.

## DynamoDB:

Banco de dados NoSQL utilizado para armazenar dados com alta escalabilidade e baixa latência. Provavelmente usado aqui para armazenar dados transacionais ou de sessão.

## AWS IAM:

Gerencia identidades e acessos aos recursos da AWS, aplicando boas práticas de segurança, como o uso de políticas de permissão mínima.

## AWS CloudTrail:

Monitora e registra atividades de API na conta da AWS para auditoria e rastreamento de alterações.

## AWS CloudWatch:

Serviço de monitoramento usado para coletar e visualizar métricas da infraestrutura, como desempenho das instâncias EC2 e do ELB.

## AWS Backup:

Centraliza e automatiza backups de dados críticos, como DynamoDB e S3, para recuperação de desastres.

## AWS CloudFormation:
Gerencia infraestrutura como código, permitindo a criação e atualização automatizada da arquitetura, garantindo consistência e eficiência.

## Interação entre os Componentes
Usuários acessam a aplicação por meio do Route 53, que resolve o DNS e direciona para o CloudFront.
O CloudFront busca arquivos estáticos no S3 ou encaminha solicitações dinâmicas para o Elastic Load Balancer, que distribui o tráfego entre as instâncias EC2 em diferentes zonas de disponibilidade.
As instâncias EC2 interagem com o DynamoDB para armazenamento e recuperação de dados transacionais.
IAM controla o acesso aos recursos, garantindo segurança.
CloudTrail registra as atividades, enquanto CloudWatch monitora métricas e desempenho.
CloudFormation provisiona e gerencia toda a infraestrutura.

# Boas Práticas Implementadas
## Alta Disponibilidade:

Uso de múltiplas zonas de disponibilidade para as instâncias EC2.
ELB distribui tráfego para evitar sobrecarga em uma única instância.
Escalabilidade:

Auto Scaling para ajustar a capacidade com base na demanda.
DynamoDB suporta aumento dinâmico de capacidade para grandes volumes de dados.

##  Segurança:

ACM para SSL/TLS, protegendo a comunicação.
IAM e CloudTrail para controle de acesso e auditoria.
Custo-Eficiência:

Uso de CloudFront para reduzir custos de transferência e melhorar a experiência do usuário.

## Sugestões de Melhorias

## Caching no DynamoDB:

Implementar o DynamoDB Accelerator (DAX) para reduzir a latência em leituras frequentes.

## Arquitetura sem servidor:

Substituir as instâncias EC2 por AWS Lambda, reduzindo custos para cargas de trabalho menos consistentes.

## Segurança Avançada:

Adicionar AWS WAF para proteger contra ataques comuns, como SQL Injection.

## Gerenciamento de Custos:

Integrar o AWS Cost Explorer para analisar custos e identificar oportunidades de otimização.
