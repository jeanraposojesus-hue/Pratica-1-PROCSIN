# 🎵 Aula Prática 1 — Processamento de Sinais I
### Processamento de Sinais I

---

## 📋 Descrição

Este repositório contém a resolução completa da **Aula Prática 1** da disciplina **Processamento de Sinais I**. O objetivo é explorar conceitos fundamentais de sinais e sistemas no domínio do tempo por meio de programação em Python, com foco na geração, visualização, escuta e processamento de sinais de áudio.

As atividades foram desenvolvidas em um notebook **Google Colab / Jupyter**, cobrindo desde sinais sintéticos simples até a simulação computacional de ambientes acústicos reais via convolução.

---

## 📁 Estrutura do Repositório

```
📦 Pratica-1-PROCSIN/
├── 📓 Prática1.ipynb          # Notebook principal com todo o código e análises
├── 📄 Aula_Prática_1.pdf      # Enunciado oficial da prática
├── 🔊 data_handel.wav         # Áudio: trecho do Messias de Handel
├── 🔊 data_h_banheiro.wav     # Áudio: resposta ao impulso de um banheiro
├── 🔊 data_sinal_taca.wav     # Áudio: percussão de uma taça de cristal
└── 📝 README.md               # Este arquivo
```

---

## 🧪 Questões Resolvidas

### Questão 1 — Sinais Senoidais
Geração do sinal `x(t) = cos(2πft)` com `fs = 44.1 kHz` e duração de 5 s, para três frequências:

| Frequência | Período | Percepção |
|---|---|---|
| 500 Hz | 2,0 ms | Tom grave |
| 5.000 Hz | 0,2 ms | Tom médio-agudo |
| 10.000 Hz | 0,1 ms | Tom muito agudo |

---

### Questão 2 — Sinais Chirp
Geração de sinais de varredura de frequência (`f0 = 500 Hz → f1 = 10.000 Hz`, 5 s) com três métodos:

- **Linear** — frequência cresce uniformemente no tempo
- **Quadrático** — frequência cresce com lei de 2ª ordem
- **Logarítmico** — oitavas percorridas por unidade de tempo são constantes *(mais natural ao ouvido humano)*

---

### Questão 3 — Áudio Real: `handel.wav`
Leitura e reprodução do sinal de Handel em três condições:

- `rate = fs` → reprodução normal
- `rate = 2 × fs` → velocidade dobrada, tom uma oitava acima
- `rate = 4 × fs` → velocidade quadruplicada, tom duas oitavas acima

---

### Questão 4 — Resposta ao Impulso de uma Sala *(Teórica)*
Descrição do procedimento para medir a **Room Impulse Response (RIR)** de qualquer ambiente, com análise dos métodos:
- Disparo / estouro de balão
- Sequência MLS (*Maximum Length Sequence*)
- **Sine Sweep** *(método mais robusto — padrão industrial)*

---

### Questão 5 — Análise dos Sinais de Áudio
Visualização e escuta dos sinais `h_banheiro.wav` e `sinal_taca.wav` no domínio do tempo, com análise de suas características temporais distintas.

---

### Questão 6 — Convolução e Simulação Acústica
Simulação de como os sinais de áudio soariam dentro do banheiro, por meio da convolução discreta:

```
y[n] = x[n] * h[n]
```

**Etapas implementadas:**
1. Reamostrar os sinais para uma frequência comum (`22.050 Hz`)
2. Calcular a convolução com `np.convolve()`
3. Normalizar o resultado para evitar *clipping*

---

## 🛠️ Tecnologias Utilizadas

| Biblioteca | Uso |
|---|---|
| `numpy` | Geração de vetores de tempo e operações matemáticas |
| `scipy.signal` | Geração de chirps e reamostagem (`resample_poly`) |
| `scipy.io.wavfile` | Leitura de arquivos `.wav` |
| `matplotlib` | Visualização dos sinais no domínio do tempo |
| `IPython.display` | Reprodução de áudio interativa no Colab |

---

## ▶️ Como Executar

### Opção 1 — Google Colab *(recomendado)*
1. Acesse o notebook pelo badge abaixo
2. Faça upload dos arquivos `.wav` na pasta `/content/`
3. Execute as células em ordem (`Runtime > Run all`)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jeanraposojesus-hue/Pratica-1-PROCSIN/blob/main/Prática1.ipynb)

### Opção 2 — Localmente
```bash
# Clone o repositório
git clone https://github.com/jeanraposojesus-hue/Pratica-1-PROCSIN.git
cd Pratica-1-PROCSIN

# Instale as dependências
pip install numpy scipy matplotlib ipython

# Abra o notebook
jupyter notebook Prática1.ipynb
```

> ⚠️ **Atenção:** ao executar localmente, substitua os caminhos `/content/` pelos caminhos relativos dos arquivos `.wav` no seu sistema.

---

## 📌 Conceitos-Chave

- **Teorema de Nyquist-Shannon** — a frequência de amostragem deve ser ao menos o dobro da frequência máxima do sinal
- **Sistema LTI** — sistema Linear e Invariante no Tempo, completamente caracterizado pela sua resposta ao impulso `h[n]`
- **Convolução discreta** — operação fundamental que relaciona entrada, saída e resposta ao impulso de sistemas LTI
- **Reamostagem** — processo essencial ao convolucionar sinais com taxas de amostragem distintas
- **RIR (Room Impulse Response)** — caracterização acústica completa de um ambiente físico

---

## 👤 Autor

**Jean Raposo**  
Curso de Engenharia de Controle e Automação  
Disciplina: Processamento de Sinais I

---

## 📄 Licença

Distribuído para fins educacionais. Uso livre para estudo e referência acadêmica.
