# 🧠 Large Language Models (LLMs) — UFMG

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.11+">
  <img src="https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/OpenAI-Tiktoken-412991?style=for-the-badge&logo=openai&logoColor=white" alt="Tiktoken">
  <img src="https://img.shields.io/badge/Jupyter-Lab%20%2F%20Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/UFMG-PPGCC-003366?style=for-the-badge" alt="UFMG">
</p>

Repositório dedicado às atividades práticas, exercícios e trabalhos (**Practical Assignments — PAs**) desenvolvidos para a disciplina de **Large Language Models (LLMs)** do Programa de Pós-Graduação em Ciência da Computação / Informática da **Universidade Federal de Minas Gerais (UFMG)**.

---

## 👤 Autor
* **Aluno:** Cristiano Gregory Monfrim Camandaroba
* **E-mail:** [cristianogregorymc@gmail.com](mailto:cristianogregorymc@gmail.com)
* **Instituição:** Universidade Federal de Minas Gerais (UFMG)
* **Curso:** Mestrado em Ciência da Computação / Informática

---

## 📊 Status das Atividades Práticas (PAs)

| Atividade | Título / Tema Principal | Status | Notebook Principal |
| :--- | :--- | :---: | :--- |
| **PA1** | Setup & Validação de Ambiente | ✅ Concluído | [`PA1/01x-setup.ipynb`](./PA1/01x-setup.ipynb) |
| **PA2** | Preparação de Dados, BPE & DataLoaders | ✅ Concluído | [`PA2/02x-data.ipynb`](./PA2/02x-data.ipynb) |
| **PA3** | *A definir* | ⏳ Em breve | — |

---

## 📂 Estrutura do Repositório

```text
LLMs_Disciplina_UFMG/
│
├── README.md                                 # Documentação geral do repositório
├── .gitignore                                # Arquivos e pastas ignorados pelo Git
│
├── PA1/                                      # Practical Assignment 1: Setup & Validação de Ambiente
│   ├── 01x-setup.ipynb                       # Notebook de teste e validação de bibliotecas
│   ├── python_environment_check.py           # Script de validação automática das versões requeridas
│   ├── requirements.txt                      # Dependências mínimas do projeto
│   ├── pyproject.toml                        # Configuração do projeto e dependências (uv/pip)
│   ├── uv.lock                               # Lockfile de dependências gerenciado via uv
│   └── Enviar_professor_moodle/              # Notebooks formatados para entrega no Moodle
│       ├── 01x-setup.ipynb
│       └── 01x_setup_remoto.ipynb
│
├── PA2/                                      # Practical Assignment 2: Preparação de Dados e Embeddings
│   ├── 02x-data.ipynb                        # Atividade prática: BPE em palavras OOV e PyTorch DataLoader
│   ├── ch02_embeding.ipynb                   # Estudo do Cap. 2 (Working with Text Data - Raschka)
│   ├── ch02_Embedding_Fazendo_Sozinho.ipynb  # Implementação guiada do pipeline de tokenização e embeddings
│   └── the-verdict.txt                       # Texto base (The Verdict - Edith Wharton) para testes
│
└── PA3/                                      # Practical Assignment 3 (Em breve)
```

---

## 📖 Detalhamento das Atividades Práticas

### 📌 PA1 — Setup e Validação de Ambiente
* **Objetivo:** Configuração, isolamento e validação do ambiente de desenvolvimento Python para o curso de LLMs.
* **Principais implementações:**
  * Configuração de ambiente virtual com `venv` e `uv`.
  * Verificação de versões mínimas de pacotes essenciais (`torch >= 2.3.0`, `tiktoken >= 0.5.1`, `tensorflow >= 2.18.0`, `numpy`, `pandas`, `tqdm`).
  * Teste de suporte a aceleração por hardware (CUDA/GPU) no PyTorch.
  * Execução de operações básicas com tensores, arrays e estruturas de dados.

---

### 📌 PA2 — Preparação de Dados e Embeddings de Texto
* **Objetivo:** Compreender e implementar as etapas fundamentais de pré-processamento de texto, tokenização e preparação de dados para treinamento de LLMs baseadas na arquitetura GPT.
* **Principais implementações:**
  1. **Byte Pair Encoding (BPE) & Palavras Fora do Vocabulário (OOV):**
     * Utilização da biblioteca `tiktoken` com a codificação do GPT-2 (`gpt2`).
     * Análise do comportamento de divisão de palavras raras/OOV em sub-palavras (*subwords*) a partir de trechos de *"The Time Machine"* (H. G. Wells).
     * Mapeamento e identificação de divisões:
       * `Traveller` $\rightarrow$ `['Trave', 'ller']`
       * `expounding` $\rightarrow$ `['exp', 'ounding']`
       * `recondite` $\rightarrow$ `['rec', 'ond', 'ite']`
       * `twinkled` $\rightarrow$ `['tw', 'ink', 'led']`
  2. **Data Loader com Janela Deslizante para Next-Token Prediction:**
     * Criação de classe customizada `DatasetGPT_aula(Dataset)` e função geradora de `DataLoader`.
     * Geração de pares $(x, y)$ onde $x$ é a sequência de entrada de tamanho `max_length` e $y$ é a sequência deslocada em 1 posição (*target*).
     * Comparação e análise de contagem de batches/exemplos com diferentes hiperparâmetros:
       * **Configuração 1:** `batch_size=4`, `max_length=2`, `stride=1` $\rightarrow$ **168 exemplos** (42 lotes de 4).
       * **Configuração 2:** `batch_size=4`, `max_length=6`, `stride=2` $\rightarrow$ **82 exemplos teóricos / 80 utilizáveis** (20 lotes de 4, com 2 exemplos descartados por `drop_last=True`).
  3. **Pipeline de Embeddings:**
     * Mapeamento de IDs de tokens para vetores densos (*Token Embeddings* via `torch.nn.Embedding`).
     * Adição de informação de posição (*Positional Embeddings*).

---

## 🛠️ Tecnologias e Bibliotecas Principais

* **Linguagem:** Python 3.11+
* **Deep Learning:** [PyTorch](https://pytorch.org/) (com suporte a aceleração por GPU/CUDA), [TensorFlow](https://www.tensorflow.org/)
* **Tokenização & NLP:** [tiktoken](https://github.com/openai/tiktoken) (OpenAI Byte Pair Encoding)
* **Ambiente Interativo:** [JupyterLab / IPython Notebooks](https://jupyter.org/)
* **Manipulação e Visualização de Dados:** NumPy, Pandas, Matplotlib, tqdm
* **Gerenciador de Pacotes:** [uv](https://github.com/astral-sh/uv) / pip

---

## 🚀 Como Configurar e Executar

### 1. Clonar o repositório
```bash
git clone https://github.com/Camandaroba06/LLMs_Disciplina_UFMG.git
cd LLMs_Disciplina_UFMG
```

### 2. Criar e ativar o ambiente virtual

**Opção A — Com `uv` (Recomendado):**
```bash
uv venv
# No Windows:
.venv\Scripts\activate
# No Linux/macOS:
source .venv/bin/activate

uv sync
```

**Opção B — Com `venv` padrão:**
```bash
# No Windows (PowerShell):
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# No Linux/macOS:
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Instalar as dependências

```bash
pip install -r PA1/requirements.txt
```

> **Nota para aceleração por GPU (NVIDIA CUDA):**  
> Para instalar a versão do PyTorch com suporte a CUDA no Windows:
> ```powershell
> pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124
> ```

### 4. Validar o ambiente

Execute o script de verificação para garantir que todas as bibliotecas estão nas versões esperadas:

```bash
python PA1/python_environment_check.py
```

### 5. Executar os Notebooks

Inicie o JupyterLab ou VS Code para navegar e executar os notebooks:

```bash
jupyter lab
```

---

## 📚 Referências

* Raschka, Sebastian. *Build a Large Language Model (From Scratch)*. Manning Publications, 2024. [Repositório Oficial](https://github.com/rasbt/LLMs-from-scratch)
* Disciplina de Large Language Models — Departamento de Ciência da Computação (DCC) / UFMG.
