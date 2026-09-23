# Proposta de Consultoria – Expansão da Capacidade de Abastecimento (Bunkering) da Buena Vista Energy

**Cliente:** Buena Vista Energy (BVE) · **Consultoria:** [Nome da consultoria] – Grupo G102
**Data:** 23/09/2026 · **Validade da proposta:** 30 dias · **Duração:** 10 semanas (23/09 a 02/12/2026)
**Equipe:** Guilherme Barbosa Padoan (Gerente de Projeto, 13682614), Pedro Henrique Menegatti Martini (Modelador Sênior, 11858133), Renan Gutemberg Costa (Desenvolvedor de Simulação, 15554441), Victor de Assis Gonçalves Santos (Analista de Dados, 11261170)

## 1. Formulação do problema

A BVE abastece navios no Porto Mar Azul com barcaças. A frota tem 6 barcaças de 3.000 t, carregadas em um terminal com 2 berços simultâneos; depois do carregamento, cada barcaça vai até o navio atracado e bombeia o combustível. A demanda cresce e o cliente quer **ampliar a capacidade do sistema em 20%**, sem perder o nível de serviço, escolhendo a alternativa técnica e economicamente mais viável.

O problema não se resolve com planilhas de médias. Chegadas de navios, janelas de atracação, tempos de carregamento, deslocamento e bombeamento são variáveis, e as barcaças disputam os berços do terminal. Isso gera filas, esperas e ociosidade que só a simulação de eventos discretos representa. A hipótese inicial, a ser verificada, é que o gargalo esteja no carregamento (2 berços × ~15 h para 3.000 t a 200 t/h) ou na frota; a simulação dirá qual.

Nota: a carta cita "Porto Mar Azul" e "Porto Brasil Sul". Assumimos que são o mesmo porto e pedimos confirmação.

## 2. Objetivo

Avaliar, por simulação computacional, cenários de expansão e recomendar a configuração de melhor custo-benefício que sustente **+20% de capacidade**.

**Definição operacional de capacidade** (a validar com o cliente): maior demanda de combustível (t/mês) atendida mantendo, no mínimo, o nível de serviço do cenário-base (percentual de atendimentos dentro da janela de atracação e tempo médio de espera do navio). Expansão de 20% = cenário com demanda 1,2 × a atual atendida sem piorar esses indicadores.

**Indicadores de desempenho:**
1. Vazão atendida (t/mês) e capacidade máxima sustentável;
2. Percentual de atendimentos dentro da janela e atraso total ponderado;
3. Tempo médio de espera do navio pela barcaça;
4. Utilização dos berços e das barcaças; fila no terminal;
5. Custo incremental da alternativa e custo por tonelada adicional.

## 3. Escopo

**Inclui:** modelo de simulação (Python/SimPy) do ciclo completo: demanda de navios, abastecimento pelas barcaças, carregamento no terminal e coordenação da operação (PCO, com a regra de programação praticada); calibração e validação do cenário-base; teste das alternativas da carta: (a) mais berços, (b) até 3 barcaças adicionais, (c) maior vazão de bombeamento, (d) regras operacionais (sequenciamento, priorização de navios); análise econômica simplificada.

**Não inclui:** otimização matemática exata da programação (MILP); projeto de engenharia civil dos berços; dinâmica do canal de navegação e do tráfego portuário; avaliação ambiental e regulatória; implantação das mudanças.

**Premissas:** o cliente fornece dados históricos e de custos a tempo (ver Solicitação de Dados); há acesso a um especialista de operações para validação; uma visita técnica ao terminal.

## 4. Método

Seguimos as etapas clássicas de um estudo de simulação: (1) formulação e definição de escopo; (2) coleta de dados e (3) modelagem conceitual, em paralelo; (4) implementação computacional; (5) verificação e validação contra o histórico da BVE; (6) planejamento de experimentos (réplicas, aquecimento, fatorial fracionado dos cenários); (7) execução e análise com intervalos de confiança; (8) documentação e recomendação. A regra de programação hoje adotada (ordenar pedidos pelo fim da janela, alocar às barcaças minimizando deslocamentos, priorizar passageiros) entra no modelo como o cenário-base.

## 5. Entregas

| # | Entrega | Semana |
|---|---------|--------|
| E1 | Proposta, modelo conceitual e solicitação de dados | 1 |
| E2 | Modelo computacional do cenário-base (código) | 4 |
| E3 | Relatório de verificação e validação | 6 |
| E4 | Plano de experimentos e cenários | 7 |
| E5 | Relatório técnico com todos os cenários simulados | 9 |
| E6 | Recomendação detalhada, dados e aplicações, e apresentação final | 10 |

## 6. Cronograma

| Etapa | Horas | S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 | S10 |
|-------|:----:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:---:|
| Formulação e proposta | 20 | ● | | | | | | | | | |
| Coleta de dados | 30 | ● | ● | ● | ● | | | | | | |
| Modelagem conceitual | 25 | ● | ● | | | | | | | | |
| Implementação (SimPy) | 50 | | ● | ● | ● | ● | | | | | |
| Verificação e validação | 30 | | | | ● | ● | ● | | | | |
| Planejamento de experimentos | 15 | | | | | | ● | ● | | | |
| Execução e análise | 30 | | | | | | | ● | ● | ● | |
| Documentação e apresentação | 25 | | | | | | | | | ● | ● |
| Gestão do projeto | 15 | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| **Total** | **240** | | | | | | | | | | |

Marco principal: modelo-base validado até o fim da semana 6. A visita técnica ocorre na semana 3.

## 7. Equipe e orçamento

Disponibilidade: 4 integrantes × 6 h/semana × 10 semanas = **240 h**.

| Papel | Responsabilidade | Horas | Valor-hora (R$) | Subtotal (R$) |
|-------|------------------|:-----:|:---------------:|--------------:|
| Gerente de Projeto | Escopo, cliente, cronograma, relatório final | 60 | 220 | 13.200 |
| Modelador Sênior | Modelo conceitual, V&V, experimentos | 60 | 180 | 10.800 |
| Desenvolvedor de Simulação | Implementação em SimPy, cenários | 60 | 150 | 9.000 |
| Analista de Dados | Coleta, tratamento, distribuições, análise econômica | 60 | 120 | 7.200 |
| **Subtotal de mão de obra** | | **240** | | **40.200** |
| Visita técnica e deslocamentos | | | | 1.800 |
| **Total da proposta** | | | | **R$ 42.000** |

Condições de pagamento sugeridas: 30% na aprovação, 40% na entrega do modelo validado (E3), 30% na entrega final (E6). Custos de licenças não existem: as ferramentas usadas são de código aberto.

## 8. Riscos principais

| Risco | Mitigação |
|-------|-----------|
| Atraso ou baixa qualidade dos dados | Dados prioritários na solicitação; uso de distribuições da literatura com sinalização |
| Definição de capacidade não acordada | Validar a definição operacional na semana 1 |
| Complexidade da regra de programação real | Modelar a regra documentada e testar variações como cenários |
| Limite de 6 h/semana por integrante | Trabalho em paralelo (dados × modelo) e escopo fechado |

Aceite: assinatura do cliente sobre esta proposta libera o início das atividades.
