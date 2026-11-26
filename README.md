# 📘 AVA3 – Consenso Distribuído em Pagamentos

**Projeto acadêmico – Sistemas Distribuídos**

Projeto desenvolvido em Python para estudar e comparar estratégias de replicação e consenso distribuído em um sistema fictício de pagamentos digitais. O trabalho reúne duas práticas: a comparação entre políticas de confirmação por unanimidade e maioria e a implementação de protocolos de replicação primário-secundário e baseado em quórum.

---

## 🎯 Objetivos

O objetivo é analisar como diferentes estratégias de replicação se comportam diante de falhas de servidores, partições de rede e recuperação de nós, considerando consistência, disponibilidade, latência e tolerância a falhas.

O projeto está dividido em duas partes:

- **Prática 1 – Unanimidade x Maioria:** simulação com cinco réplicas para comparar as políticas de confirmação de pagamentos.
- **Prática 2 – Protocolos de replicação:** implementação e comparação dos protocolos primário-secundário e baseado em quórum, utilizando um simulador de eventos discretos.

## 🛠️ Tecnologias utilizadas

- Python 3.9 ou superior — execução de referência com Python 3.12.
- Biblioteca padrão do Python.
- Matplotlib — geração dos gráficos.
- Arquivos CSV e TXT — armazenamento dos resultados e registros dos experimentos.

## 🔄 Modificações realizadas na AVA3

Na Prática 1, foram realizadas as alterações solicitadas na atividade guiada:

1. **Alteração do pagamento P002:** valor modificado de R$ 20,00 para R$ 25,00.
2. **Alteração da partição de rede:** configuração original de 2 + 3 modificada para 3 + 2, com os grupos `{N0,N1,N2}` e `{N3,N4}`.
3. **Comparação das versões:** execução da versão original da aula e da versão modificada para analisar os efeitos das alterações.

As modificações estão identificadas no código pelo comentário `# AVA3`.

Na Prática 2, foram implementados dois protocolos próprios de replicação:

- **Primário-secundário:** replicação de escritas, heartbeat, detecção de falhas e eleição de um novo primário.
- **Baseado em quórum:** operações de leitura e escrita com quóruns, versionamento e resolução de conflitos.

## 📂 Estrutura do projeto

A estrutura abaixo apresenta os principais arquivos e diretórios utilizados na entrega:

```text
AVA3-Consenso-Distribuido/
│
├── README.md
├── pratica3_consenso_pagamentos_ava3.py
├── ava3_protocolos.py
├── gerar_graficos_ava3.py
│
├── resultados/
│   ├── pratica1_original.csv
│   ├── pratica1_ava3.csv
│   ├── resumo.csv
│   └── eventos_semente1.txt
│
├── figuras/
│   └── gráficos gerados para o relatório
│
└── docs/
    └── AVA3_VictorGuilherme.pdf
```

*Observação: a estrutura acima representa os principais arquivos mencionados no relatório. Os arquivos e subdiretórios devem corresponder exatamente aos que estiverem presentes no repositório.*

## ▶️ Como executar o projeto

### 1. Pré-requisitos

Instale o Python 3.9 ou superior.

Para gerar os gráficos, instale o Matplotlib:

```bash
pip install matplotlib
```

Ou, caso exista um arquivo `requirements.txt` na versão disponibilizada:

```bash
pip install -r requirements.txt
```

### 2. Executar a Prática 1 – Versão modificada

```bash
python pratica3_consenso_pagamentos_ava3.py
```

Executa a simulação com as políticas de unanimidade e maioria, utilizando as alterações realizadas na AVA3.

### 3. Executar somente a política de maioria

```bash
python pratica3_consenso_pagamentos_ava3.py --politica maioria
```

Executa a simulação considerando apenas a política de confirmação por maioria.

### 4. Executar a versão original da atividade

```bash
python pratica3_consenso_pagamentos_ava3.py --versao original
```

Executa os cenários com os parâmetros originais da aula, permitindo comparar os resultados com a versão modificada.

### 5. Executar a Prática 2 – Protocolos de replicação

```bash
python ava3_protocolos.py
```

Executa os cenários dos protocolos primário-secundário e baseado em quórum, utilizando 30 sementes aleatórias por cenário.

### 6. Executar a demonstração comentada

```bash
python ava3_protocolos.py --demo
```

Apresenta uma demonstração dos eventos simulados, facilitando a compreensão do funcionamento dos protocolos.

### 7. Gerar os gráficos

```bash
python gerar_graficos_ava3.py
```

Gera as figuras utilizadas na análise dos resultados do relatório, a partir dos arquivos produzidos pelas simulações.

**Observação:** no Windows, também é possível utilizar `py` no lugar de `python`.

## 📊 Resultados obtidos

### Prática 1 – Comparação entre unanimidade e maioria

Os resultados financeiros da versão original e da versão modificada foram:

| Política de confirmação | Versão original | Versão AVA3 |
|---|---:|---:|
| Unanimidade (5/5) | R$ 60,00 | R$ 60,00 |
| Maioria (3/5) | R$ 170,00 | R$ 175,00 |

Na versão modificada, o total confirmado pela política de maioria aumentou R$ 5,00 devido à alteração do valor de P002. Na unanimidade, o total permaneceu igual, pois essa transação não alcançou as cinco confirmações necessárias.

A alteração da partição de 2 + 3 para 3 + 2 não modificou os status das operações, mas alterou a distribuição dos nós entre os grupos e a posição do líder em relação à maioria.

### Prática 2 – Comparação dos protocolos

Na segunda prática, foram realizadas 540 execuções dos cenários principais e das configurações de quórum, além de 60 execuções do cenário de concorrência.

Os experimentos avaliaram:

- Tempo de detecção de falhas.
- Tempo de eleição de um novo primário.
- Retomada das operações de escrita.
- Maior intervalo sem escrita confirmada.
- Tempo de ressincronização dos nós.
- Disponibilidade e latência.
- Leituras desatualizadas e conflitos.
- Pagamentos confirmados perdidos.
- Quantidade de mensagens trocadas.

Os resultados indicaram diferenças entre os protocolos. O primário-secundário depende da detecção da falha e da eleição de um novo primário para retomar as escritas quando o líder falha. Já o protocolo baseado em quórum pode continuar atendendo operações enquanto houver nós suficientes para formar o quórum exigido.

Os valores detalhados, as médias, os desvios-padrão e as análises dos cenários estão apresentados no relatório.

## 📈 Gráficos e resultados visuais

O script `gerar_graficos_ava3.py` produz as figuras utilizadas para analisar os experimentos.

Os gráficos apresentam comparações relacionadas a:

- Resultados financeiros das versões original e modificada da Prática 1.
- Arquitetura dos protocolos implementados.
- Latência e comportamento das escritas durante falhas.
- Disponibilidade das operações nos diferentes cenários.
- Comparação de métricas de detecção e recuperação.

As figuras geradas complementam as tabelas e as análises apresentadas no relatório.

## ⚠️ Limitações do projeto

O projeto é uma simulação didática executada em um único ambiente Python. Portanto:

- Não utiliza comunicação real entre servidores pela rede.
- Não representa servidores físicos ou processos independentes.
- Não realiza pagamentos reais.
- Utiliza eventos, atrasos de mensagens e relógio lógico para representar o comportamento de um sistema distribuído.
- Os tempos apresentados são milissegundos simulados, não medições de uma rede real.
- As implementações são didáticas e não representam implementações completas de produção de protocolos como Raft ou Paxos.

Os resultados devem ser interpretados considerando as características e limitações do modelo simulado.

## 📄 Relatório

O relatório completo apresenta a fundamentação teórica, a metodologia, os cenários de falha, os resultados experimentais, os gráficos e a análise comparativa dos protocolos.

Arquivo: `docs/AVA3_VictorGuilherme.pdf`

## 👨‍💻 Autor

**Victor Guilherme**

Atividade prática AVA3 – Sistemas Distribuídos.

---

*Projeto desenvolvido para fins acadêmicos e educacionais.*
