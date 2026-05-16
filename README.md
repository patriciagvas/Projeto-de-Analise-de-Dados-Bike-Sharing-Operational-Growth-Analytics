# Projeto de Análise de Dados Bike Sharing Operational e Growth-Analytics

Este projeto tem como objetivo analisar o comportamento dos usuários, a eficiência operacional e a integridade dos dados de uma plataforma de compartilhamento de bicicletas. A análise combina o poder de manipulação de dados em larga escala do **SQL Server** com a flexibilidade do **Python** para extrair indicadores críticos de performance (KPIs) voltados a engajamento, retenção (MoM) e logística de frotas.

## Fontes de dados:

* Tabela rides: contém informações de cada corrida realizada com as bicicletas do serviço;
* Tabela stations: contém informações sobre cada estação do serviço;
* Tabela users: contém informações sobre cada usuário do serviço;

## Etapas do projeto:

* Carregamento das 3 fontes de dados em formato.csv para o notebook;
* Verificação dos dados quanto a valores nulos, duplicatas e tipos de dados;
* Conexão com o SQL Server via pyodbc;
* Criação do banco de dados Stationbikes;
* Criação de tabelas e inserção de seus respectivos dados;
* Consultas SQL para análises de negócio;

## Ferramentas utilizadas:

* Python (Pandas, pyodbc);
* SQL Server;

## Perguntas de negócio:

  1. Existe algum usuário cadastrado na tabela users que nunca realizou uma viagem?
  2. Padrão de Uso (Horário): Em qual hora do dia ocorre o maior volume de viagens?
  3. Rotas Populares: Quais são os 5 pares de estações (origem e destino) que mais aparecem nas viagens?
  4. Análise de Retenção (Mês a Mês).
   5. Tempo de Inatividade entre Viagens
   6. Quem são os usuários que mais percorreram distância e qual o seu perfil predominante (*Commuter* vs. *Explorador*)?
   7. Identifique os horários com maior total de corridas por estação.
   8.  Análise de Retenção e Cohort

## Insights e recomendações:

**1. Engajamento e ciclo de vida do usuário:**

* A análise indica que  todos os usuários cadastrados na plataforma possuem pelo menos uma viagem realizada, ou seja,  o processo de onboarding do aplicativo é altamente eficaz em converter novos cadastros em usuários ativos de forma imediata.
  
* A taxa de retenção mensal (MoM) ao longo de 2024 manteve-se estável entre 66% e 72%, indicando que o produto está maduro no mercado e possui forte aderência do público, ou seja, a maior parte da base de usuários enxerga valor contínuo no serviço.

* Contudo, a análise de inatividade revelou que os usuários passam, em média, entre 10 e 30 dias inativos entre uma corrida e outra. Além disso, não há variação significativa nesse valor ao analisar em nível de faixa etária ou tipo de assinatura, em que há em média 22 dias de inatividade. A partir desse insight recomenda-se criar uma estratégia de recuperação de engajamento via email ou notificação push para alertar o usuário quando atingir 15 dias sem usar o serviço, oferecendo alguns incentivos para reduzir essa janela de tempo.
  
**2. Eficiência Operacional e Logística:**

* Os usuários tendem a usar mais o serviço no período vespertino, que concentra 7687 corridas, com um pico operacional entre 15 e 16 horas. O segundo período com maior pico ocorre entre 6 horas e 7 horas. Esses horários indicam que os clientes provavelmente usam o serviço de bicicletas para ida e volta de trabalho, escola/faculdade.

* Com base nos dados de capacidade e total de corridas por período, recomenda-se expandir a capacidade das principais estações nos horários de pico para evitar falta de bicicletas disponíveis para os clientes.

**3.Perfil dos Power Users (O Top 1%):**

* A maioria dos Top usuários do serviço são do tipo Commuters, ou seja, que fazem em média 8km por viagem, comprovando que os clientes que mais recorrentes da plataforma utilizam as biciletas como condução diária e não para lazer.
* Além disso, o tempo de atividade média dos usuários é de 160 dias, demonstrando que há um ciclo de relacionamento de aproximadamente 5 meses.
* Com base nesses inisghts, recomeda-se criar planos de assinatura focados em benefícios de mobilidade urbana diária para os Power users, como, por exemplo, descontos corporativos a fim de aumentar o tempo de retenção e satisfação dos clientes. 

**4. Governança e Qualidade de Dados:**

Como mencionado anteriormente, foi encontrada uma anomalia na ingestão dos dados de 973 usuários, em que a data de encerramento da viagem é inferior à data de criação da conta na plataforma. Portanto, é necessário reportar o caso ao time de engenharia de dados para solicitar auditação das tabelas de origem, investigando qual falha de sincronização de fusos horários ou outro tipo de erro possa estar ocasionando essa anomalia. 

   
