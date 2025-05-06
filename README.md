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

<img src="https://github.com/agodoi/m12-semana04/blob/main/imgs/taxaFalhavsTempo.png" width="500">

#### 3. Colaboração interfuncional
Desenvolvedores e operadores trabalham juntos, compartilhando métricas, responsabilidades e decisões.

#### 4. Resiliência e recuperação rápida
Incidentes são monitorados e resolvidos com mais rapidez.

#### 5. Inovação com segurança
A automação reduz riscos humanos, permitindo deploys frequentes e seguros.

🧠 Cultura DevOps = Comunicação + Colaboração + Feedback + Confiança + Automação

### 💬 Discussão
Quais métricas vocês acham que ajudam a provar que um time está melhorando sua entrega ao longo do tempo?

<img src="https://github.com/agodoi/m12-semana04/blob/main/imgs/graficoSubida.png" width="500">

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 📊 Quadro Comparativo — Métricas de DevOps

| **Métrica**                        | **O que mede**                                             | **Por que é útil**                                                                 |
|-----------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------|
| **Lead Time**                     | Tempo do commit ao deploy                                   | Avalia a eficiência de entrega; menor tempo = maior agilidade                      |
| **Frequência de Implantação**     | Nº de deploys por período                                   | Indica a capacidade de entrega contínua e feedback rápido                          |
| **Taxa de Sucesso dos Testes**    | % de testes automatizados que passam                        | Reflete a estabilidade do código e qualidade dos testes                            |
| **Cobertura de Código**           | % do código coberto por testes                              | Ajuda a garantir que o código está minimamente validado por testes                 |
| **MTTR (Tempo Médio de Recuperação)** | Tempo para restaurar o sistema após falha              | Mede a resiliência e capacidade de resposta a incidentes                           |
| **Taxa de Falhas de Mudança**     | % de deploys que causam falhas                              | Mostra a confiabilidade das entregas                                               |
| **Duração do Build**              | Tempo necessário para concluir o processo de build          | Ajuda a identificar gargalos no pipeline                                           |

### Exemplos Práticos das Principais Métricas de CI/CD

#### 🕒 Lead Time (Tempo de Entrega)
Definição: Tempo entre o commit do desenvolvedor e a entrega em produção.
<br>
**Exemplo:**
João fez um commit às 10h da manhã. Após passar pelo pipeline (build, testes, revisão, deploy), a funcionalidade foi ao ar às 14h.
<br>
🟢 Lead Time = 4 horas

---
#### 📈 Frequência de Implantação (Deploy Frequency)
Definição: Quantas vezes o time entrega código em produção num determinado período.
<br>
**Exemplo:**
Na última semana, o time fez 12 deploys no ambiente de produção.
<br>
🟢 Frequência de Implantação = 12 por semana

---
#### ❌ Taxa de Falhas de Mudança (Change Failure Rate)
Definição: Porcentagem de mudanças implantadas que causaram falha.
<br>
**Exemplo:**
De 10 deploys feitos, 2 causaram erros em produção e precisaram de correção imediata.
<br>
🟠 Taxa de Falhas de Mudança = 20%

---
#### 🔧 Tempo Médio de Recuperação (MTTR)
Definição: Tempo médio para restaurar o sistema após uma falha em produção.
<br>
**Exemplo:**
Um bug derrubou o sistema às 15h, e foi resolvido às 15h40.
<br>
🟢 MTTR = 40 minutos

---
#### 🧪 Cobertura de Código
Definição: Percentual do código coberto por testes automatizados.
<br>
**Exemplo:**
Com uso de JaCoCo, o time viu que 78% das funções têm testes automatizados.
<br>
🟢 Cobertura = 78%

---
#### ✅ Taxa de Sucesso dos Testes
Definição: Percentual de testes que passaram em uma execução.
<br>
**Exemplo:**
Num pipeline com 200 testes, 192 passaram.
<br>
🟢 Taxa de Sucesso = 96%

---
#### 🧱 Duração do Build
Definição: Tempo necessário para compilar e empacotar a aplicação.
<br>
**Exemplo:**
O GitHub Actions indica que a execução do job de build leva 7 minutos.
<br>
🟢 Duração do Build = 7 minutos

---
#### 💥 Taxa de Falhas de Implantação
Definição: Porcentagem de implantações que falham no processo de deploy.
<br>
**Exemplo:**
De 5 execuções do job de deploy, 1 falhou por erro de configuração.
<br>
🟠 Taxa de Falhas de Implantação = 20%



## 🎯 2. Fundamentos das Métricas de CI/CD

### O que são Métricas de CI/CD?

As métricas de CI/CD são indicadores extraídos das etapas de Integração Contínua (CI) e Entrega Contínua (CD) de um pipeline de desenvolvimento de software. 

Elas servem para medir e analisar o desempenho, a qualidade e a confiabilidade dos processos de construção, teste e entrega de software.

Em outras palavras: as métricas dizem como está o “batimento cardíaco” do seu time DevOps.

Essas métricas ajudam a entender:

* Se o código está funcionando bem
* Se o processo de entrega está rápido
* Se há falhas recorrentes
* Se o time está evoluindo ou estagnado


### 🚀 Por que essas métricas são importantes? 

#### 1) Tomada de decisão baseada em dados
   
* Evita decisões por “achismo”.
* Permite ajustes precisos nos processos do time.

#### 2) Melhoria Contínua
   
* Identifica pontos de gargalo e desperdício.
* Serve como bússola para onde melhorar: build, testes, tempo de deploy, etc.**

#### 3) Qualidade e Confiabilidade

* Monitora a estabilidade das versões entregues.
* Reduz riscos ao automatizar testes e deploys.

#### 4) Visibilidade e transparência

* Todos os membros do time enxergam a performance do pipeline e do produto.

### 📊 Categorias de Métricas
Para facilitar o entendimento e aplicação, as métricas de CI/CD podem ser agrupadas em quatro categorias principais:

| **Categoria**  | **O que avalia**                                   | **Exemplos de Métricas**                               |
|----------------|-----------------------------------------------------|---------------------------------------------------------|
| **Eficiência** | Velocidade e produtividade do time                 | Lead Time, Duração do Build                             |
| **Estabilidade** | Frequência e impacto de falhas                   | Taxa de Falhas de Mudança, MTTR                         |
| **Tempo**      | Tempo total para concluir tarefas ou processos     | Tempo para Corrigir Testes, Tempo de Deploy             |
| **Cobertura**  | Qualidade e abrangência dos testes                 | Cobertura de Código, Taxa de Sucesso dos Testes         |


#### 💡Exemplo aplicado

Imagine um time com entregas lentas e builds demorando 20 minutos:

* Eficiência: está baixa (duração do build alta).
* Cobertura: pode estar impactando, se muitos testes são lentos.
* Com métricas bem definidas, o time identifica onde focar: otimizar testes ou dividir builds.

#### 🧠 Pergunta para debate em sala:
Se você tivesse que escolher uma única métrica para monitorar a saúde do seu pipeline, qual escolheria? E por quê?

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>


---

### 4. Instrumentação com GitHub Actions

O **GitHub Actions** é uma poderosa plataforma de automação para CI/CD, e oferece acesso a logs, tempos de execução e status dos jobs de forma nativa. Isso permite que várias métricas sejam extraídas diretamente dos seus workflows.

As principais métricas que podem ser instrumentadas diretamente:


| **Métrica**                    | **Como obter com GitHub Actions**                                                                                             |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **Lead Time**                  | Usando timestamps do commit + deploy nos workflows                                                                            |
| **Duração do Build**           | Usando logs de tempo de execução (`job.started_at` e `job.completed_at`)                                                      |
| **Taxa de Sucesso dos Testes** | Interpretando resultados de testes automatizados (ex: `jest`, `pytest`, `JUnit`) com `exit codes` e `actions/upload-artifact` |
| **Cobertura de Código**        | Usando ferramentas como JaCoCo, Codecov ou Coveralls integradas ao pipeline                                                   |
| **Tempo para Corrigir Testes** | Comparando falhas em runs anteriores com execuções que voltaram a passar                                                      |



#### 🕒 Lead Time

**Como medir:** timestamps do commit e do deploy
<br>
**Exemplo prático:** um aluno faz um commit às 09h00 da manhã. O workflow executa testes e build automaticamente. O job de deploy ocorre às 11h15 no ambiente de staging.
<br>
🟢 Lead Time = 2h15min
<br>
Você pode registrar o horário do commit com github.event.head_commit.timestamp e o horário do fim do deploy com steps.deploy.completed_at.

---
#### 🧱 Duração do Build

**Como medir:** tempo entre início e fim do job de build no GitHub Actions
<br>
**Exemplo prático:** o job de build começou às 14h02 e terminou às 14h09. No log do GitHub Actions, isso aparece automaticamente com o tempo total do job.
<br>
🟢 Duração do Build = 7 minutos
<br>
Exibido direto no summary do GitHub Actions. Pode ser registrado em uma métrica com Prometheus.

---
#### ✅ Taxa de Sucesso dos Testes
**Como medir:** verificando exit codes dos frameworks de teste (ex: pytest, jest) e interpretando os relatórios
<br>
**Exemplo prático:** um job de testes executa 120 testes com pytest. 117 testes passaram e 3 falharam.
<br>
🟢 Taxa de Sucesso = 97,5%
<br>
Os resultados podem ser salvos com actions/upload-artifact, analisados com test-reporter ou enviados ao Codecov.

---
#### 🧪 Cobertura de Código
**Como medir:** usando ferramentas como JaCoCo, Codecov ou Coveralls integradas ao CI
<br>
**Exemplo prático:** o time configura JaCoCo em um projeto Java. Após o teste, JaCoCo gera um relatório: 80% das classes estão cobertas por testes.
<br>
🟢 Cobertura de Código = 80%
<br>
O relatório pode ser enviado ao Codecov via GitHub Actions com um token e mostrado em forma de badge no README.

---
#### 🔁 Tempo para Corrigir Testes
**Como medir:** comparar tempo entre a falha de um teste e a execução posterior que passou.
<br>
**Exemplo prático:** pipeline executada às 10h falha por causa de testes com jest. Alguém corrige o erro e faz novo push às 13h. O pipeline passa com 100% dos testes.
<br>
🟢 Tempo para Corrigir Testes = 3 horas 
<br>
Você pode escrever um script que busca no histórico do Actions (via API) a última falha e o primeiro sucesso subsequente para esse mesmo job/teste.




### 🧪 5. Aplicação Prática no Repositório

#### 🎯 Objetivo

Aplicar métricas de CI/CD no seu projeto usando GitHub Actions, extraindo dados como duração do build, cobertura de código e taxa de sucesso de testes, e exibindo essas informações diretamente no repositório via badges ou dashboards.

#### 🧩 Etapa 1 — Criação de um workflow no GitHub Actions

📁 Crie o arquivo: .github/workflows/ci-metrics.yml

```
mkdir -p .github/workflows
touch .github/workflows/ci-metrics.yml

```
✏️ Insira o conteúdo base do workflow [yaml]:

```
name: CI com Métricas

on:
  push:
    branches: [main]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Início do job
      run: echo "JOB_STARTED_AT=$(date +%s)" >> $GITHUB_ENV

    - name: Instalar dependências
      run: npm install

    - name: Rodar testes com cobertura
      run: |
        npm run test -- --coverage
        echo "TEST_SUCCESS=$?" >> $GITHUB_ENV

    - name: Enviar cobertura para Codecov
      uses: codecov/codecov-action@v3
      with:
        token: ${{ secrets.CODECOV_TOKEN }}

    - name: Fim do job
      run: echo "JOB_ENDED_AT=$(date +%s)" >> $GITHUB_ENV

    - name: Calcular duração
      run: |
        DURATION=$(( $JOB_ENDED_AT - $JOB_STARTED_AT ))
        echo "BUILD_DURATION=$DURATION" >> $GITHUB_ENV
        echo "⏱️ Duração: $DURATION segundos"
```

#### 🧩 Etapa 2 — Armazenamento e visualização das métricas

🧪 Cobertura de Código com Codecov

* Crie uma conta no [https://codecov.io/](https://codecov.io/)
* Registre seu repositório
* Copie o token do projeto no painel
* Adicione ao GitHub: vá em Settings > Secrets > Actions → Novo segredo
* Nome: CODECOV_TOKEN
* Valor: (o token que copiou)

🎯 Exibir Badge no README
* Após o primeiro push com cobertura, vá ao painel do Codecov
* Copie o badge em formato Markdown
* Cole no topo do seu README.md:

```
![Cobertura de Código](https://codecov.io/gh/USUARIO/REPO/branch/main/graph/badge.svg)
```

Substitua **USUARIO** e **REPO** com seu nome de usuário e nome do repositório.

🧩 Etapa 3 — Documentação das Métricas no Repositório
No README.md ou em uma pasta /docs/, documente:

markdown
Copiar
Editar
## 📊 Métricas de CI/CD Monitoradas

- **Lead Time:** calculado por diferença entre horário de commit e execução do job.
- **Duração do Build:** registrada automaticamente em segundos.
- **Cobertura de Código:** coletada com Codecov.
- **Taxa de Sucesso dos Testes:** interpretada via código de saída dos testes.
- **Tempo para Corrigir Testes:** pode ser avaliado comparando o tempo entre a falha e a correção.

📌 Os relatórios estão disponíveis nos logs do GitHub Actions e no painel do Codecov.





### 6. Definindo Métricas com GQM/ATAM

Método Goal-Question-Metric (GQM)

Método ATAM para avaliação de trade-offs de arquitetura

Como aplicar esses métodos para selecionar métricas no contexto do projeto da turma
