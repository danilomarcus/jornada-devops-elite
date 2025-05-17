# Jornada DevOps Elite

## Sobre o Projeto
Este projeto faz parte da Jornada DevOps Elite, demonstrando a implementação de aplicações em Kubernetes com monitoramento usando Prometheus e Grafana, em ambiente cloud usando pipeline CI/CD com github actions.

## Estrutura do Projeto
- **01-conversao-temperatura**: Aplicação NodeJS para conversão de temperatura
- **02-review**: Aplicação de revisão de filmes com PostgreSQL
- **03-web-color**: Aplicação web com diferentes variações de cores
- **04-prometheus**: Configuração do Prometheus e exportadores
- **05-dashboard**: Dashboards para o Grafana

## Componentes Principais
- Kubernetes para orquestração de contêineres
- PostgreSQL como banco de dados
- Prometheus para monitoramento
- Grafana para visualização de métricas
- Exportadores para coleta de métricas específicas (postgres_exporter)

## Configuração do Ambiente

### Pré-requisitos
- Docker desktop
- kubectl
- SO Mac, Linux or WSL2 (Windows)

### Instalação

1. Clone o repositório:
   ```
   git clone <repo>
   cd jornada-devops-elite
   ```

2. Aplique os manifestos do Kubernetes:
   ```
   kubectl apply -f 02-review/k8s/deployment.yaml (apenas local para testes)
   kubectl apply -f 03-web-color/web-deployment.yaml (apenas local para testes)
   kubectl apply -f 04-prometheus/deployment.yaml 
   kubectl apply -f 04-prometheus/postgres-exporter.yaml
   ```

3. Configure o Prometheus e Grafana:
   ```
   # Acessar a URL do grafana e obter a senha pelo terminal:
    kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo   
   ```

## Monitoramento

### PostgreSQL
Para visualizar as métricas do PostgreSQL no Grafana:
1. Certifique-se de que o postgres-exporter está em execução
2. No Grafana, importe um dos dashboards disponíveis em `05-dashboard/` ou use os IDs:
   - 9628: PostgreSQL Database
   - 455: PostgreSQL Overview
   - 14331: PostgreSQL Statistics

## Aplicações

### Review de Filmes (02-review)
Aplicação .NET que permite cadastrar e visualizar revisões de filmes, armazenando os dados no PostgreSQL.

### Web Color (03-web-color)
Aplicação web simples para demonstrar escalonamento e balanceamento de carga no Kubernetes.

## Licença
MIT