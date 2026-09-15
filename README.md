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
