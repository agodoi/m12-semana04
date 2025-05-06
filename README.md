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

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

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


### 🎯 2. Fundamentos das Métricas de CI/CD

#### O que são Métricas de CI/CD?

As métricas de CI/CD são indicadores extraídos das etapas de Integração Contínua (CI) e Entrega Contínua (CD) de um pipeline de desenvolvimento de software. 

Elas servem para medir e analisar o desempenho, a qualidade e a confiabilidade dos processos de construção, teste e entrega de software.

Em outras palavras: as métricas dizem como está o “batimento cardíaco” do seu time DevOps.

Essas métricas ajudam a entender:

* Se o código está funcionando bem
* Se o processo de entrega está rápido
* Se há falhas recorrentes
* Se o time está evoluindo ou estagnado

#### 🚀 Por que essas métricas são importantes?

1) Tomada de decisão baseada em dados
   
* Evita decisões por “achismo”.
* Permite ajustes precisos nos processos do time.

2) Melhoria Contínua
   
* Identifica pontos de gargalo e desperdício.
* Serve como bússola para onde melhorar: build, testes, tempo de deploy, etc.**

3) Qualidade e Confiabilidade

* Monitora a estabilidade das versões entregues.
* Reduz riscos ao automatizar testes e deploys.

4) Visibilidade e transparência

* Todos os membros do time enxergam a performance do pipeline e do produto.

📊 Categorias de Métricas
Para facilitar o entendimento e aplicação, as métricas de CI/CD podem ser agrupadas em quatro categorias principais:

Categoria	O que avalia	Exemplos de Métricas
Eficiência	Velocidade e produtividade do time	Lead Time, Duração do Build
Estabilidade	Frequência e impacto de falhas	Taxa de Falhas de Mudança, MTTR
Tempo	Tempo total para concluir tarefas ou processos	Tempo para Corrigir Testes, Tempo de Deploy
Cobertura	Qualidade e abrangência dos testes	Cobertura de Código, Taxa de Sucesso dos Testes

💡 Exemplo aplicado
Imagine um time com entregas lentas e builds demorando 20 minutos:

Eficiência: está baixa (duração do build alta).

Cobertura: pode estar impactando, se muitos testes são lentos.

Com métricas bem definidas, o time identifica onde focar: otimizar testes ou dividir builds.

🧠 Pergunta para debate em sala:
Se você tivesse que escolher uma única métrica para monitorar a saúde do seu pipeline, qual escolheria? E por quê?





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
