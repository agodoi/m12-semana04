## Atendimento do Professor

### Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!

# SLA e Métricas

SLA & Métricas são indicadores que auxiliam gestores e times de desenvolvimento a definir a estratégia de evolução e na operção dos produtos de software que mantém as empresas ativas. Nesta instrução iremos recuperar estes conceitos importantes na rotina de engenharia de software.

## (1) SLA (Service Level Agreement) 

Uma SLA (Service Level Agreement), ou Acordo de Nível de Serviço, é um compromisso formal entre duas partes — normalmente entre um fornecedor de serviço (como uma equipe de software ou empresa de TI) e um cliente (usuário, empresa contratante ou equipe interna) — que define quais níveis de desempenho, disponibilidade e suporte são esperados de um serviço.

### (1.1) ✅ Para que serve uma SLA?

a) Estabelecer expectativas claras: define o que o serviço vai garantir (por exemplo, 99,9% de disponibilidade, tempo de resposta de até 500ms, tempo máximo para resolver falhas).

b) Formalizar compromissos técnicos: tira o acordo do “achismo” e transforma-o em um contrato mensurável e rastreável.

c) Aumentar a confiança entre as partes: mostra que o fornecedor se compromete com qualidade, e o cliente sabe o que pode cobrar.

d) Proteger ambas as partes: serve como base jurídica para acordos comerciais e evita conflitos por mal-entendidos.

e) Orientar o monitoramento e a melhoria contínua: permite que SLIs (indicadores reais) sejam acompanhados para garantir que os SLOs (objetivos) estão sendo cumpridos.

**📌 Exemplo prático:**

“Nossa API de autenticação terá no mínimo 99,9% de disponibilidade por mês, com tempo médio de resposta inferior a 600ms, e qualquer falha crítica será resolvida em até 1 hora.”

### (1.2) Outros tipos de Acordos

#### (1.2.1) SLO — Service Level Objective (Objetivo de Nível de Serviço)

É um objetivo interno e mensurável de performance ou confiabilidade. O SLO é o alvo que a equipe técnica ou a organização se compromete a alcançar regularmente, servindo como base para o SLA (mas nem todo SLO vira SLA).

**Exemplo:** “Queremos que 95% das requisições sejam respondidas em menos de 400ms.”

#### (1.2.2) SLI — Service Level Indicator (Indicador de Nível de Serviço)

É uma métrica real coletada do sistema, usada para verificar se o SLO está sendo atingido. O SLI é o dado cru medido por ferramentas de monitoramento (como Prometheus, Grafana, Datadog, etc.).

**Exemplo:** “Na última semana, a latência média foi de 380ms, e 96,2% das requisições foram respondidas em menos de 400ms.


| Conceito | Papel no ciclo                                                  |
| -------- | --------------------------------------------------------------- |
| **SLI**  | Métrica observada (realidade medida)                            |
| **SLO**  | Meta desejada baseada nos SLIs                                  |
| **SLA**  | Acordo formal que define o que é garantido e suas consequências |



### (1.3) 📄 Exemplo de SLA: API de Autenticação

**Descrição do Serviço**: a API de Autenticação é responsável por validar usuários e fornecer tokens de acesso para os sistemas internos e externos da plataforma.

| **Métrica**                         | **Valor Garantido** | **Descrição**                                                                 |
| ----------------------------------- | ------------------- | ----------------------------------------------------------------------------- |
| **Disponibilidade Mensal**          | 99,9%               | O serviço estará disponível pelo menos 99,9% do tempo em cada mês calendário. |
| **Tempo Máximo de Resposta**        | 500ms               | Tempo máximo para resposta da API em 95% das requisições.                     |
| **Tempo de Recuperação (MTTR)**     | Até 30 minutos      | Em caso de falha crítica, o serviço será restabelecido em até 30 minutos.     |
| **Janela de Manutenção Programada** | Sábados, 2h às 4h   | Manutenção poderá ser feita sem impacto no SLA se ocorrer nesse período.      |


### (1.4) 📌 Fórmula geral para dois serviços interdependentes:

Se:

Serviço A tem SLA = 99,9% (ou 0,999)

Serviço B tem SLA = 99,5% (ou 0,995)

Então:

SLA final = SLA_A × SLA_B
          = 0,999 × 0,995
          = 0,994005 → 99,4005%

Essa abordagem reflete a probabilidade de ambos estarem disponíveis ao mesmo tempo, pois em sistemas em série, se um falha, o sistema como um todo falha.


### (1.5) 📄 Exemplo Completo de SLA

### A. 🧾 Descrição do Serviço

Este SLA se aplica ao serviço de **API de Autenticação**, responsável por validar usuários e fornecer tokens de acesso. O serviço será monitorado continuamente para garantir conformidade com os níveis acordados.

---

### B. 🎯 Nível de Serviço Acordado

| **Métrica**                    | **Valor Garantido**              | **Descrição**                                                            |
|-------------------------------|----------------------------------|--------------------------------------------------------------------------|
| **Disponibilidade mensal**    | 99,9%                            | O serviço estará disponível pelo menos 99,9% do tempo por mês            |
| **Tempo de resposta médio**   | ≤ 500ms                          | Média de tempo para resposta da API em 95% das requisições              |
| **Tempo máximo para recuperação (MTTR)** | ≤ 30 minutos         | Tempo máximo para restabelecimento após falha crítica                    |
| **Janela de manutenção**      | Sábados, entre 2h e 4h           | Período reservado para manutenção sem impacto no SLA                     |

---

### C. 📏 Cálculo de Disponibilidade

| **Nível de SLA** | **Máximo de indisponibilidade permitida (30 dias)** |
|------------------|-----------------------------------------------------|
| 99,0%            | 7h12min                                            |
| 99,9%            | ~43min                                              |
| 99,99%           | ~4,3min                                               |

> Cálculo: `(1 - SLA) × minutos no mês (30 dias = 43.200 minutos)`

---

### D. ⚖️ Penalidades por Descumprimento

| **Disponibilidade Real** | **Crédito concedido ao cliente**       |
|---------------------------|----------------------------------------|
| 99,0% a 99,8%             | 10% de desconto no valor mensal        |
| Abaixo de 99,0%           | 25% de desconto no valor mensal        |

[CONTRATO AWS EC2](https://aws.amazon.com/pt/compute/sla/)

---

### E. 🧾 Exceções (Não contabilizam violação de SLA)

- Falhas causadas por erro de configuração do cliente
- Ataques DDoS não mitigáveis
- Desastres naturais ou eventos de força maior
- Interrupções causadas durante a janela de manutenção programada

---

### F. 📊 Monitoramento e Medição

As métricas serão monitoradas continuamente por ferramentas como:
- **Prometheus** para disponibilidade e latência
- **Grafana** para dashboards em tempo real
- **Sentry** para rastreamento de erros em produção

Relatórios mensais serão gerados com base nos **SLIs (Service Level Indicators)** para verificar conformidade com os **SLOs (Service Level Objectives)** definidos.

[AWS Status](https://health.aws.amazon.com/health/status)

[Azure Status](https://azure.status.microsoft/pt-br/status)

[Airbnb Status](https://airbnbapi.statuspage.io/)

[Google Status](https://status.cloud.google.com/?hl=pt-br)

---

### G. 🔗 Validade do SLA

Este SLA entra em vigor a partir de sua assinatura e permanecerá válido enquanto o serviço estiver em operação, podendo ser revisto mediante acordo entre as partes.



<br><br><br><br><br>


## (2) Introdução ao DevOps e à Cultura de Métricas

### (2.1) 🛠️ O que é DevOps (visão além da automação)

DevOps é uma abordagem cultural, organizacional e técnica que integra as equipes de desenvolvimento (Dev) e operações (Ops) com o objetivo de entregar software de forma mais rápida, confiável e contínua.

Embora muitas pessoas associem DevOps apenas à automação de builds e deploys, o verdadeiro valor do DevOps está na colaboração entre pessoas, na quebra de silos organizacionais e na entrega de valor contínuo ao usuário final.

🔎 Exemplo: Em vez de uma equipe de desenvolvimento passar o código para outra equipe “resolver” o deploy, ambas colaboram desde o início, com pipelines automatizados, testes contínuos e visibilidade compartilhada.

### (2.2) 🌍 Benefícios organizacionais e culturais do DevOps

Adotar DevOps vai além de ferramentas como GitHub Actions, Jenkins ou Azure DevOps. Trata-se de transformar a cultura da empresa ou do time:

#### (2.2.1) Agilidade na entrega de valor
Reduz o tempo entre escrever o código e entregá-lo ao usuário final.

#### (2.2.2) Melhoria da qualidade do software
Ao incluir testes automatizados e feedback contínuo, a chance de bugs em produção diminui.

<img src="https://github.com/agodoi/m12-semana04/blob/main/imgs/taxaFalhavsTempo.png" width="500">

#### (2.2.3) Colaboração interfuncional
Desenvolvedores e operadores trabalham juntos, compartilhando métricas, responsabilidades e decisões.

#### (2.2.4) Resiliência e recuperação rápida
Incidentes são monitorados e resolvidos com mais rapidez.

#### (2.2.5) Inovação com segurança
A automação reduz riscos humanos, permitindo deploys frequentes e seguros.

🧠 Cultura DevOps = Comunicação + Colaboração + Feedback + Confiança + Automação

### (2.3)💬 Discussão
Quais métricas vocês acham que ajudam a provar que um time está melhorando sua entrega ao longo do tempo?

<img src="https://github.com/agodoi/m12-semana04/blob/main/imgs/graficoSubida.png" width="500">

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### (2.4) 📊 Quadro Comparativo — Métricas de DevOps

| **Métrica**                        | **O que mede**                                             | **Por que é útil**                                                                 |
|-----------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------|
| **Lead Time**                     | Tempo do commit ao deploy                                   | Avalia a eficiência de entrega; menor tempo = maior agilidade                      |
| **Frequência de Implantação**     | Nº de deploys por período                                   | Indica a capacidade de entrega contínua e feedback rápido                          |
| **Taxa de Sucesso dos Testes**    | % de testes automatizados que passam                        | Reflete a estabilidade do código e qualidade dos testes                            |
| **Cobertura de Código**           | % do código coberto por testes                              | Ajuda a garantir que o código está minimamente validado por testes                 |
| **MTTR (Tempo Médio de Recuperação)** | Tempo para restaurar o sistema após falha              | Mede a resiliência e capacidade de resposta a incidentes                           |
| **Taxa de Falhas de Mudança**     | % de deploys que causam falhas                              | Mostra a confiabilidade das entregas                                               |
| **Duração do Build**              | Tempo necessário para concluir o processo de build          | Ajuda a identificar gargalos no pipeline                                           |

### (2.5) Exemplos Práticos das Principais Métricas de CI/CD

#### (2.5.1) 🕒 Lead Time (Tempo de Entrega)
Definição: Tempo entre o commit do desenvolvedor e a entrega em produção.
<br>
**Exemplo:**
João fez um commit às 10h da manhã. Após passar pelo pipeline (build, testes, revisão, deploy), a funcionalidade foi ao ar às 14h.
<br>
🟢 Lead Time = 4 horas

---
#### (2.5.2) 📈 Frequência de Implantação (Deploy Frequency)
Definição: Quantas vezes o time entrega código em produção num determinado período.
<br>
**Exemplo:**
Na última semana, o time fez 12 deploys no ambiente de produção.
<br>
🟢 Frequência de Implantação = 12 por semana

---
#### (2.5.3) ❌ Taxa de Falhas de Mudança (Change Failure Rate)
Definição: Porcentagem de mudanças implantadas que causaram falha.
<br>
**Exemplo:**
De 10 deploys feitos, 2 causaram erros em produção e precisaram de correção imediata.
<br>
🟠 Taxa de Falhas de Mudança = 20%

---
#### (2.5.4) 🔧 Tempo Médio de Recuperação (MTTR)
Definição: Tempo médio para restaurar o sistema após uma falha em produção.
<br>
**Exemplo:**
Um bug derrubou o sistema às 15h, e foi resolvido às 15h40.
<br>
🟢 MTTR = 40 minutos

---
#### (2.5.5) 🧪 Cobertura de Código
Definição: Percentual do código coberto por testes automatizados.
<br>
**Exemplo:**
Com uso de JaCoCo, o time viu que 78% das funções têm testes automatizados.
<br>
🟢 Cobertura = 78%

---
#### (2.5.6) ✅ Taxa de Sucesso dos Testes
Definição: Percentual de testes que passaram em uma execução.
<br>
**Exemplo:**
Num pipeline com 200 testes, 192 passaram.
<br>
🟢 Taxa de Sucesso = 96%

---
#### (2.5.7) 🧱 Duração do Build
Definição: Tempo necessário para compilar e empacotar a aplicação.
<br>
**Exemplo:**
O GitHub Actions indica que a execução do job de build leva 7 minutos.
<br>
🟢 Duração do Build = 7 minutos

---
#### (2.5.8) 💥 Taxa de Falhas de Implantação
Definição: Porcentagem de implantações que falham no processo de deploy.
<br>
**Exemplo:**
De 5 execuções do job de deploy, 1 falhou por erro de configuração.
<br>
🟠 Taxa de Falhas de Implantação = 20%



### 🎯 2. Fundamentos das Métricas de CI/CD

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
