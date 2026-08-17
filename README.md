# 🧠 Large Language Models (LLMs) — UFMG

Repositório dedicado às atividades práticas, exercícios e trabalhos práticos (**Practical Assignments — PAs**) desenvolvidos para a disciplina de **Large Language Models (LLMs)** do Programa de Pós-Graduação em Ciência da Computação / Informática da **Universidade Federal de Minas Gerais (UFMG)**.

---

## 👤 Autor
* **Aluno:** Cristiano Gregory Monfrim Camandaroba
* **E-mail:** [cristianogregorymc@gmail.com](mailto:cristianogregorymc@gmail.com)
* **Instituição:** Universidade Federal de Minas Gerais (UFMG)

---

## 📂 Estrutura do Repositório

```text
LLMs_Disciplina_UFMG/
│
├── README.md                           # Documentação geral do repositório
├── .gitignore                          # Arquivos e pastas ignorados pelo Git
│
├── PA1/                                # Practical Assignment 1: Setup & Validação de Ambiente
│   ├── 01x-setup.ipynb                 # Notebook de teste e validação de ambiente
│   ├── python_environment_check.py     # Script de validação das dependências
│   ├── requirements.txt                # Lista de dependências com versões requeridas
│   ├── pyproject.toml                  # Configuração do projeto e dependências (uv/pip)
│   ├── uv.lock                         # Lockfile de dependências
│   └── Enviar_professor_moodle/        # Notebooks e relatórios formatados para entrega
│
├── PA2/                                # Practical Assignment 2 (Em breve)
└── PA3/                                # Practical Assignment 3 (Em breve)
```

---

## 🛠️ Tecnologias e Bibliotecas Principais

* **Linguagem:** Python 3.11+
* **Deep Learning:** [PyTorch](https://pytorch.org/) (com suporte a aceleração por GPU/CUDA), [TensorFlow](https://www.tensorflow.org/)
* **Tokenização & NLP:** [tiktoken](https://github.com/openai/tiktoken)
* **Ambiente Interativo:** [JupyterLab / IPython](https://jupyter.org/)
* **Manipulação e Visualização de Dados:** NumPy, Pandas, Matplotlib, tqdm

---

## 🚀 Como Configurar e Executar

### 1. Clonar o repositório
```bash
git clone https://github.com/Camandaroba06/LLMs_Disciplina_UFMG.git
cd LLMs_Disciplina_UFMG
```

### 2. Criar e ativar o ambiente virtual

**No Windows (PowerShell):**
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**No Linux/macOS:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

*(Ou utilizando o gerenciador **[uv](https://github.com/astral-sh/uv)**: `uv venv` e `uv sync`)*

### 3. Instalar as dependências

```bash
# Para a PA1:
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

---

## 📚 Referências

* Raschka, Sebastian. *Build a Large Language Model (From Scratch)*. Manning Publications.
* Disciplina de Large Language Models — UFMG.
