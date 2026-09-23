# Solicitação de Dados – Projeto BVE

**Para:** Equipe Gestora – Buena Vista Energy · **De:** Grupo G102 · **Data:** 23/09/2026 · **Versão:** 1.0
**Período histórico solicitado:** últimos 12 meses (mínimo 6). **Formato preferido:** planilha (.xlsx/.csv), uma linha por evento. Prioridade: **A** = necessário para o modelo-base; **M** = melhora o modelo ou serve à análise de cenários.

Dados hipotéticos ou estimativas de especialistas são aceitos, desde que identificados como tais.

## 1. Demanda (navios)

| ID | Dado | Unidade / formato | Uso no modelo | Prior. |
|----|------|-------------------|---------------|:------:|
| D1 | Data/hora de cada pedido de abastecimento | data-hora | Processo de chegada | A |
| D2 | Data/hora de chegada e de saída do navio (atracação/desatracação) | data-hora | Janela e tempo no porto | A |
| D3 | Terminal/berço de atracação de cada pedido | código | Destino e deslocamento | A |
| D4 | Volume pedido e volume entregue | t | Duração do serviço | A |
| D5 | Janela de abastecimento acordada [início, fim] | data-hora | Atraso e nível de serviço | A |
| D6 | Tipo de navio e prioridade (passageiro, data acordada) | categoria | Regra de priorização | A |
| D7 | Pedidos rejeitados ou cancelados, com motivo | data-hora, texto | Demanda não atendida | M |
| D8 | Previsão de crescimento da demanda | % a.a. | Cenários futuros | M |

## 2. Abastecimento (barcaças)

| ID | Dado | Unidade / formato | Uso no modelo | Prior. |
|----|------|-------------------|---------------|:------:|
| B1 | Frota: capacidade, vazão de bombeamento, velocidade | t, t/h, km/h | Parâmetros dos recursos | A |
| B2 | Tempo de atracação, conexão e inspeção (início do serviço) | h | Tempo de setup | A |
| B3 | Tempo de medição, desconexão e desatracação | h | Tempo de encerramento | A |
| B4 | Tempo de bombeamento medido por operação | h | Validação de a / vazão | A |
| B5 | Matriz de distâncias terminal BVE × terminais do porto | km | Tempos de deslocamento | A |
| B6 | Registros de posição e horários das barcaças (AIS/operador) | data-hora, lat/long | Calibração de viagens | M |
| B7 | Paradas e manutenção: frequência e duração | h | Disponibilidade | M |
| B8 | Custo diário de afretamento/operação e custo de nova barcaça | R$/dia, R$ | Análise econômica | A |

## 3. Carregamento (terminal BVE)

| ID | Dado | Unidade / formato | Uso no modelo | Prior. |
|----|------|-------------------|---------------|:------:|
| T1 | Número de berços e vazão de carregamento (por berço e total) | un., t/h | Capacidade do terminal | A |
| T2 | Data/hora de chegada, início e fim de carregamento de cada barcaça | data-hora | Fila e tempo de carga | A |
| T3 | Volume carregado por ciclo | t | Carga da barcaça | A |
| T4 | Tempos de atracação, setup e liberação do berço | h | Ocupação do berço | A |
| T5 | Disponibilidade e estoque dos tanques de combustível | t | Restrição de abastecimento | M |
| T6 | Paradas do terminal (manutenção, clima) | h | Disponibilidade | M |
| T7 | Custo e prazo de ampliar berços e vazão | R$, meses | Análise econômica | A |

## 4. Coordenação (PCO)

| ID | Dado | Unidade / formato | Uso no modelo | Prior. |
|----|------|-------------------|---------------|:------:|
| P1 | Regras de programação e priorização em uso (descrição) | texto | Regra do cenário-base | A |
| P2 | Horários e horizonte de programação | h | Frequência de decisão | A |
| P3 | Programação planejada × realizada por ciclo | data-hora | Aderência e validação | M |
| P4 | Eventos que causam reprogramação e frequência | tipo, contagem | Perturbações | M |
| P5 | Multas contratuais e custo de atraso por navio | R$/h | Custo do atraso | A |

## 5. Validação e desempenho atual

| ID | Dado | Unidade / formato | Uso | Prior. |
|----|------|-------------------|-----|:------:|
| V1 | Volume mensal fornecido | t/mês | Capacidade atual (referência dos +20%) | A |
| V2 | % de atendimentos dentro da janela e atraso médio | %, h | Validação do cenário-base | A |
| V3 | Espera média do navio pela barcaça | h | Validação | A |
| V4 | Utilização média de berços e barcaças | % | Validação | M |

## 6. Esclarecimentos solicitados

1. "Porto Mar Azul" e "Porto Brasil Sul" na carta são o mesmo porto?
2. A capacidade da frota é mesmo de 3.000 t por barcaça, ou há barcaças menores?
3. Como a BVE mede "capacidade" (t/mês, navios/mês, outro)? O nível de serviço atual é o mínimo aceitável para os +20%?
4. A vazão de 200 t/h por berço ou 400 t/h no total?
5. Há orçamento máximo ou restrição de espaço físico para novos berços?
6. Uma visita técnica ao terminal e a entrevista com um programador são possíveis na semana 3?
