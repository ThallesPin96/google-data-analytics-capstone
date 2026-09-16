# Cyclistic Bike-Share Analysis — Google Data Analytics Capstone

## 📊 Sobre o projeto
Este é o projeto final (capstone) do Google Data Analytics Certificate, aplicando 
todo o processo de análise de dados (Ask, Prepare, Process, Analyze, Share, Act) 
em um case study real de bike-share.

---

## 🔍 Ask — Business Task

A Cyclistic é uma empresa de bike-share em Chicago que trabalha com dois tipos de 
cliente: os **ciclistas casuais**, que pagam por passe avulso ou diário, e os 
**membros anuais**, que pagam uma assinatura. O time de marketing, liderado pela 
diretora Lily Moreno, já identificou que os membros anuais dão muito mais retorno 
financeiro pra empresa do que os casuais. Por isso, a estratégia agora é clara: em 
vez de sair atrás de clientes totalmente novos, faz mais sentido converter quem já 
usa a Cyclistic ocasionalmente em assinantes fixos.

O problema é que, pra montar uma campanha de conversão que realmente funcione, 
primeiro é preciso entender **como** esses dois grupos usam as bicicletas de forma 
diferente. Sem esse entendimento, qualquer campanha de marketing seria só um chute.

Como analista júnior do time de marketing, minha parte nesse projeto foi responder 
justamente essa pergunta:

> **Como os membros anuais e os ciclistas casuais usam as bicicletas da Cyclistic 
> de forma diferente?**

Esse recorte importa porque é a base de tudo que vem depois — as recomendações 
finais de marketing só fazem sentido se estiverem apoiadas em um entendimento 
sólido do comportamento real dos usuários, e não em suposição.

## 🗂️ Prepare — Data Sources

Para essa análise, usei os dados históricos públicos de viagens da **Divvy**, o 
sistema real de bike-share de Chicago que serviu de inspiração para o case fictício 
da Cyclistic. Os dados são disponibilizados publicamente pela Motivate International 
Inc. sob licença de uso aberto.

Baixei os **12 meses mais recentes disponíveis no momento da análise**, cobrindo o 
período de **setembro de 2025 a agosto de 2026**, totalizando cerca de **6,1 milhões 
de registros de viagens**. Cada arquivo mensal contém 13 colunas, incluindo 
identificador da viagem, tipo de bicicleta, horário de início e término, estação de 
origem e destino, coordenadas geográficas e o tipo de usuário (`member` ou `casual`).

Avaliando a credibilidade desses dados pelo critério **ROCCC**:

- **Reliable (Confiável):** dados operacionais reais, gerados automaticamente pelo 
próprio sistema de bicicletas, sem intervenção manual.
- **Original:** vêm diretamente da fonte primária (Divvy/Motivate International).
- **Comprehensive (Abrangente):** cobre um ano inteiro de operação, o que permite 
observar variações sazonais.
- **Current (Atual):** são os dados mais recentes disponibilizados publicamente.
- **Cited (Citado):** a fonte e a licença de uso são claramente identificadas.

Durante a verificação inicial, encontrei algumas limitações relevantes:

> Uma parte significativa dos registros não tem o nome ou ID da estação de início/fim 
> preenchido — provavelmente porque bicicletas elétricas podem ser destravadas e 
> travadas fora de estações fixas, via GPS.

- Por questões de privacidade, os dados não permitem identificar o usuário 
individualmente, o que impede, por exemplo, saber se um mesmo ciclista casual fez 
várias corridas avulsas ao longo do ano.
- Um dos arquivos baixados veio com o nome interno inconsistente com o mês real dos 
dados (nomeado como referente a um mês, mas contendo registros de outro). Verifiquei 
manualmente as datas dentro do arquivo para confirmar o período correto antes de 
seguir com a análise.

## 📈 Analyze — Summary of Analysis

Depois de consolidar os 12 meses de dados (setembro de 2025 a agosto de 2026), 
totalizando **6.115.982 corridas**, calculei estatísticas descritivas e cruzei os 
dados por tipo de usuário, dia da semana e sazonalidade.

### Duração das viagens: casual x member

| | Duração média | Duração máxima | Total de corridas |
|---|---|---|---|
| **Casual** | 0:20:41 | 25:59:57 | 2.160.365 |
| **Member** | 0:12:22 | 25:59:54 | 3.955.617 |

> Ciclistas casuais pedalam, em média, quase **70% mais tempo por viagem** do que 
> membros anuais — um indício forte de que os dois grupos usam a Cyclistic para 
> propósitos diferentes.

### Padrão por dia da semana

| | Dom | Seg | Ter | Qua | Qui | Sex | Sáb |
|---|---|---|---|---|---|---|---|
| **Casual** (duração média) | 0:24:17 | 0:20:43 | 0:18:02 | 0:17:15 | 0:18:02 | 0:20:12 | 0:23:10 |
| **Member** (duração média) | 0:13:29 | 0:12:04 | 0:11:55 | 0:11:51 | 0:11:55 | 0:12:18 | 0:13:36 |
| **Casual** (nº de corridas) | 348k | 258k | 247k | 248k | 268k | 335k | 457k |
| **Member** (nº de corridas) | 420k | 566k | 631k | 632k | 626k | 578k | 503k |

> Membros pedalam mais durante a **semana útil**, com picos de segunda a quinta — 
> um padrão típico de deslocamento para o trabalho. Já os casuais pedalam mais nos 
> **finais de semana**, com viagens mais longas, sugerindo uso voltado a lazer.

### Tipo de bicicleta utilizada

| | Classic bike | Electric bike |
|---|---|---|
| **Casual** | 570.304 | 1.590.061 |
| **Member** | 1.263.533 | 2.692.084 |

Ambos os grupos preferem bicicletas elétricas, mas a proporção é parecida entre 
os dois — não é um fator que diferencia claramente o comportamento.

### Sazonalidade

O volume de corridas segue um padrão sazonal claro para os dois grupos: forte queda 
nos meses de inverno em Chicago (dezembro a fevereiro) e pico nos meses de verão 
(junho a agosto). Esse padrão é mais acentuado entre os casuais, o que reforça a 
ideia de que esse grupo pedala mais por lazer — atividade naturalmente mais sensível 
ao clima — enquanto membros mantêm um uso mais constante ao longo do ano, compatível 
com deslocamento diário independente da estação.

### Observação sobre qualidade dos dados

Durante a análise, identifiquei um pequeno resíduo de 268 corridas (0,004% do total) 
categorizadas fora do período esperado, provavelmente viagens que cruzaram a virada 
do mês nos arquivos de origem. O volume é insignificante e não impacta as conclusões.
