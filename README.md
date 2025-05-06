# Atendimento do Professor

## Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!

# Semana 04 - SLA e Métricas

SLA & Métricas são indicadores que auxiliam gestores e times de desenvolvimento a definir a estratégia de evolução e na operção dos produtos de software que mantém as empresas ativas. Nesta instrução iremos recuperar estes conceitos importantes na rotina de engenharia de software.

## 1. Introdução ao DevOps e à Cultura de Métricas

### 🛠️ O que é DevOps (visão além da automação)

DevOps é uma abordagem cultural, organizacional e técnica que integra as equipes de desenvolvimento (Dev) e operações (Ops) com o objetivo de entregar software de forma mais rápida, confiável e contínua.

Embora muitas pessoas associem DevOps apenas à automação de builds e deploys, o verdadeiro valor do DevOps está na colaboração entre pessoas, na quebra de silos organizacionais e na entrega de valor contínuo ao usuário final.

🔎 Exemplo: Em vez de uma equipe de desenvolvimento passar o código para outra equipe “resolver” o deploy, ambas colaboram desde o início, com pipelines automatizados, testes contínuos e visibilidade compartilhada.

### 🌍 Benefícios organizacionais e culturais do DevOps

Adotar DevOps vai além de ferramentas como GitHub Actions, Jenkins ou Azure DevOps. Trata-se de transformar a cultura da empresa ou do time:

#### 1. Agilidade na entrega de valor
Reduz o tempo entre escrever o código e entregá-lo ao usuário final.

#### 2. Melhoria da qualidade do software
Ao incluir testes automatizados e feedback contínuo, a chance de bugs em produção diminui.

#### 3. Colaboração interfuncional
Desenvolvedores e operadores trabalham juntos, compartilhando métricas, responsabilidades e decisões.

#### 4. Resiliência e recuperação rápida
Incidentes são monitorados e resolvidos com mais rapidez.

#### 5. Inovação com segurança
A automação reduz riscos humanos, permitindo deploys frequentes e seguros.

🧠 Cultura DevOps = Comunicação + Colaboração + Feedback + Confiança + Automação

### 💬 Discussão
Quais métricas vocês acham que ajudam a provar que um time está melhorando sua entrega ao longo do tempo?










2. Fundamentos das Métricas de CI/CD
O que são métricas de CI/CD

Importância das métricas para eficiência e qualidade

Categorias: eficiência, estabilidade, tempo e cobertura

3. Principais Métricas de CI/CD
Lead Time

Frequência de Implantação

Taxa de Falhas de Mudança

Tempo Médio de Recuperação (MTTR)

Cobertura de Código

Taxa de Sucesso dos Testes

Duração do Build

Taxa de Falhas de Implantação

4. Instrumentação com GitHub Actions
Quais métricas podem ser extraídas diretamente do GitHub Actions

Limitações do GitHub Actions (o que não é possível monitorar diretamente)

Ferramentas complementares: Prometheus, Grafana, Sentry

5. Aplicação Prática no Repositório
Criação de workflows no GitHub Actions para extrair métricas (ex.: duração de build, sucesso dos testes, cobertura com JaCoCo)

Armazenamento e visualização (ex: YAML de exemplo, integração com Prometheus ou badge no README)

Documentação no repositório GitHub sobre as métricas coletadas

6. Definindo Métricas com GQM/ATAM
Método Goal-Question-Metric (GQM)

Método ATAM para avaliação de trade-offs de arquitetura

Como aplicar esses métodos para selecionar métricas no contexto do projeto da turma
