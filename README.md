# ShieldBank-AI: Detecção de Fraudes com Machine Learning 🛡️💰

Bem-vindo ao **ShieldBank-AI**. Este projeto foi desenvolvido para demonstrar a aplicação de Inteligência Artificial na segurança bancária, especificamente na identificação de transações suspeitas de fraude em cartões de crédito utilizando padrões comportamentais.

## 🎯 Objetivo do Projeto
O objetivo é ir além das regras estáticas (Ex: "bloquear tudo acima de R$ 5.000"). O ShieldBank-AI utiliza o algoritmo **Isolation Forest** para detetar anomalias estatísticas, aprendendo o que é o comportamento "normal" do utilizador e isolando o que é atípico, como compras em horários de madrugada ou locais não habituais.

## 🛠️ Ferramentas e Tecnologias (Stack)
O projeto foi construído 100% em **Python**, utilizando as bibliotecas líderes do setor financeiro e de dados:
* **Python (Core):** Lógica e integração.
* **Pandas:** Para manipulação de dados e limpeza do histórico bancário.
* **Scikit-Learn:** Para a implementação da Inteligência Artificial (Isolation Forest).
* **Matplotlib / Seaborn:** Para a criação do dashboard visual moderno.
* **NumPy:** Para geração e processamento de dados numéricos.

## 🗂️ Estrutura dos Documentos
* `gerador_transacoes.py`: Cria o cenário bancário com 1.000 transações e insere fraudes camufladas.
* `detector_fraudes.py`: O núcleo de IA que processa, normaliza e identifica os suspeitos.
* `visualizador_fraudes.py`: Gera o gráfico profissional com a separação entre transações seguras e alertas.
* `transacoes_bancarias.csv`: Base de dados gerada para o teste.
* `relatorio_fraudes.csv`: O veredito final da IA com o rótulo de cada transação.

## 🧠 Como funciona o Isolation Forest?
Diferente de modelos que aprendem o que é "correto", este algoritmo foca em **isolar** as anomalias. Como as fraudes são raras e diferentes, elas são mais fáceis de separar matematicamente. O modelo cria "florestas" de decisão; as transações que atingem um isolamento mais rápido (poucas divisões na árvore) são marcadas como suspeitas.



---

## ❓ FAQ - Perguntas Frequentes

**1. Por que não usar apenas regras simples de "IF/ELSE"?**
Regras manuais são fáceis de prever e difíceis de manter. O ShieldBank-AI consegue cruzar Valor + Hora + Local simultaneamente para encontrar padrões complexos que uma regra estática ignoraria.

**2. O que são os pontos vermelhos misturados aos azuis no gráfico?**
São os **Falsos Positivos**. O algoritmo indica que aquela transação, embora possa ser legítima, está entre os 1% mais "estranhos" do conjunto. Num banco real, isto serve para alertar o sistema de prevenção sem necessariamente bloquear o cliente de imediato.

**3. Para que serve a normalização (StandardScaler)?**
Serve para que a escala do "Valor" (R$ 5.000) não domine a escala da "Hora" (0-23h). A normalização garante que todos os dados contribuam com o mesmo peso estatístico para a IA.

**4. O modelo deteta fraudes de valor baixo?**
Sim! Se o horário e o local forem atípicos para o padrão do cliente, mesmo uma compra de valor reduzido será isolada como suspeita.

**5. O que define a sensibilidade do sistema?**
O parâmetro `contamination`. No projeto usamos 1% (0.01). Ao aumentar este valor, o banco torna-se mais rigoroso, capturando mais fraudes mas aumentando o número de alertas falsos.

**6. Como este sistema escala para milhões de dados?**
O algoritmo Isolation Forest possui uma complexidade linear, o que o torna extremamente eficiente e rápido para processar volumes massivos de transações em tempo real.

---

**Desenvolvedora:** [BiaAbaaoud](https://github.com/BiaAbaaoud)