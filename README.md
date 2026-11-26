# 📘 AVA3 – Consenso Distribuído em Pagamentos

**Projeto acadêmico – Sistemas Distribuídos**

Simulação didática de consenso distribuído aplicada a um sistema fictício de pagamentos digitais, desenvolvida em Python como parte da atividade prática AVA3.

---

## 🎯 Objetivo do projeto

O objetivo deste trabalho é analisar e comparar duas políticas de confirmação de pagamentos em um ambiente com cinco servidores (nós):

- **Unanimidade:** todos os cinco nós precisam confirmar a operação.
- **Maioria:** pelo menos três dos cinco nós precisam confirmar a operação, formando um quórum.

A simulação permite observar como essas políticas se comportam diante de falhas de servidores, partições de rede, recuperação de nós, duplicidade de transações e falha do líder.

## 🛠️ Tecnologias utilizadas

- Python 3.9 ou superior.
- Biblioteca padrão do Python.
- Matplotlib para geração dos gráficos.
- Arquivos CSV para registro dos resultados.

## 🔄 Modificações realizadas na AVA3

Em relação ao código original apresentado na atividade, foram realizadas as seguintes alterações:

1. **Alteração do pagamento P002:** o valor foi modificado de R$ 20,00 para R$ 25,00.
2. **Alteração da partição de rede:** a configuração original de 2 + 3 foi modificada para 3 + 2.
3. **Seleção de versão:** inclusão da opção `--versao` para executar os cenários originais ou modificados.
4. **Registro dos resultados:** geração de arquivos CSV separados para facilitar a comparação.
5. **Resumo financeiro:** inclusão da apresentação dos totais confirmados ao final da execução.
6. **Teste adicional de idempotência:** inclusão de um teste para verificar o comportamento de uma transação com o mesmo identificador, mas com valor diferente.

As modificações realizadas estão identificadas no código por comentários `# AVA3`.

## 📂 Estrutura do projeto

```text
AVA3-Consenso-Distribuido/
│
├── README.md
├── pratica3_consenso_pagamentos_ava3.py
├── gerar_graficos_ava3.py
├── requirements.txt
├── .gitignore
│
├── resultados/
│   ├── resultados_ava3.csv
│   ├── resultados_original.csv
│   └── resultados_ava3_maioria.csv
│
├── figuras/
│   ├── fig1_topologias.png
│   ├── fig2_confirmacoes.png
│   ├── fig3_totais.png
│   └── fig4_original_vs_ava3.png
│
└── docs/
    └── AVA3_VictorGuilherme.pdf
```

## ▶️ Como executar o projeto

### 1. Pré-requisitos

Instale o Python 3.9 ou superior.

Para gerar os gráficos, instale a dependência:

```bash
pip install matplotlib
```

Ou instale pelo arquivo de requisitos:

```bash
pip install -r requirements.txt
```

### 2. Executar a versão modificada da AVA3

```bash
python pratica3_consenso_pagamentos_ava3.py
```

Executa os cenários utilizando as políticas de unanimidade e maioria.

### 3. Executar somente a política de maioria

```bash
python pratica3_consenso_pagamentos_ava3.py --politica maioria
```

### 4. Executar a versão original da atividade

```bash
python pratica3_consenso_pagamentos_ava3.py --versao original
```

Permite comparar os cenários originais com as modificações realizadas na AVA3.

### 5. Executar o teste de ID conflitante

```bash
python pratica3_consenso_pagamentos_ava3.py --teste-id
```

Verifica se uma transação com identificador já utilizado pode ser reenviada com um valor diferente.

### 6. Gerar os gráficos

Primeiro, execute a versão AVA3 e a versão original para gerar os arquivos CSV necessários.

Depois, execute:

```bash
python gerar_graficos_ava3.py
```

As imagens serão geradas automaticamente na pasta `figuras/`.

**Observação:** no Windows, também é possível utilizar `py` no lugar de `python`.

## 📊 Resultados obtidos

Na versão modificada da AVA3, os resultados financeiros finais foram:

| Política de confirmação | Total confirmado |
|---|---:|
| Unanimidade | R$ 60,00 |
| Maioria | R$ 175,00 |

A política de maioria apresentou maior capacidade de confirmar operações durante determinados cenários de falha, desde que o quórum mínimo fosse alcançado.

A comparação entre a versão original e a versão modificada também permite observar os efeitos das alterações no valor da transação P002 e na configuração da partição de rede.

## 📈 Gráficos e resultados visuais

O projeto possui um script separado para gerar quatro figuras:

- **Figura 1:** representação das topologias de rede utilizadas.
- **Figura 2:** comparação entre confirmações obtidas e quórum mínimo exigido.
- **Figura 3:** totais financeiros e quantidade de pagamentos confirmados.
- **Figura 4:** comparação dos resultados entre a versão original e a versão AVA3.

## ⚠️ Limitações do projeto

Este trabalho apresenta uma simulação didática executada em um único processo Python.

Portanto:

- Não implementa integralmente protocolos como Raft ou Paxos.
- Não utiliza comunicação real entre servidores pela rede.
- Não representa servidores independentes.
- Não realiza pagamentos reais.
- Utiliza eventos e relógio lógico para representar o comportamento do sistema.

Os resultados devem ser interpretados dentro dos limites do modelo simulado.

## 👨‍💻 Autor

**Victor Guilherme**

Atividade prática AVA3 – Sistemas Distribuídos.

---

*Projeto desenvolvido para fins acadêmicos e educacionais.*
