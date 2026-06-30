# Tech Challenge — Fase 1 (IADT)

Projeto de Machine Learning para **classificação de risco/diagnóstico** em contexto de **saúde da mulher**, conforme enunciado da FIAP.

## Problema abordado

Classificar tumores de mama como **malignos** ou **benignos** com base em características numéricas de núcleos celulares (Wisconsin Breast Cancer).

**Fonte dos dados:** [data.csv no repositório SamirGoes/tech_challenge_1](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data/data)

| Coluna | Significado |
|--------|-------------|
| `diagnosis` | `M` = maligno, `B` = benigno |
| demais colunas | 30 medidas numéricas (raio, textura, perímetro, etc.) |

## Entrega EXTRA — Visão Computacional (CNN)

Além da parte obrigatória (dados estruturados), o grupo implementou a **entrega EXTRA** do enunciado: classificação de exames por **imagem** com **Rede Neural Convolucional (CNN)**.

| Notebook | Descrição |
|----------|-----------|
| **`notebooks/Pneumonia.ipynb`** | **EXTRA principal** — CNN para raio-x de tórax (NORMAL vs PNEUMONIA), dataset [Chest X-Ray (Kaggle)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia) |
| `notebooks/02_cnn_mamografias.ipynb` | Complementar — CNN em mamografias (CBIS-DDSM), desenvolvido no Colab |

Documentação da parte EXTRA:
- `docs/Análise dos resultados de pneumonia.pdf`
- `docs/figuras/raio-x.png` e `docs/figuras/resultados.png`

## Estrutura

```
Tech Challenge/
├── data/
│   └── data.csv                              # dataset câncer de mama (obrigatório)
├── docs/
│   ├── Relatorio_Tech_Challenge_Fase1.pdf    # relatório técnico completo
│   ├── Análise dos resultados de pneumonia.pdf
│   └── figuras/                              # gráficos dos relatórios
├── notebooks/
│   ├── 01_analise_e_modelagem.ipynb          # OBRIGATÓRIO — EDA, ML, SHAP
│   ├── Pneumonia.ipynb                       # EXTRA — CNN raio-x (visão computacional)
│   └── 02_cnn_mamografias.ipynb              # EXTRA complementar — CNN mamografias
├── requirements.txt
└── README.md
```

## Colaboração no Git (grupo)

Todos devem trabalhar a partir da branch **`main`**. No dia da entrega, o trabalho de cada um será integrado na `main` via merge.

### 1. Baixar o projeto (branch `main`)

```bash
git clone <URL-do-repositorio>
cd tech-challenge-fiap
git checkout main
git pull origin main
```

> Se o repositório já existir na sua máquina, entre na pasta do projeto e atualize a `main`:
>
> ```bash
> git checkout main
> git pull origin main
> ```

### 2. Criar sua branch a partir da `main`

Use um nome que identifique você ou a tarefa (ex.: `feature/eda-mariana`, `fix/preprocessamento-joao`):

```bash
git checkout main
git pull origin main
git checkout -b feature/sua-tarefa
```

Desenvolva, commite e envie **apenas na sua branch**:

```bash
git add .
git commit -m "descrição do que foi feito"
git push -u origin feature/sua-tarefa
```

### 3. Na entrega — merge na `main`

Quando o grupo finalizar, cada branch aprovada entra na `main` (via Pull Request no GitHub ou merge local, conforme combinarem):

```bash
git checkout main
git pull origin main
git merge feature/sua-tarefa
git push origin main
```

**Regra do grupo:** não commitar direto na `main` durante o desenvolvimento; sempre criar branch a partir da `main` atualizada e integrar na `main` só na entrega (ou quando o grupo decidir juntar as partes).

## Como executar

### Parte obrigatória — câncer de mama (ML)

```bash
cd tech-challenge-fiap
python -m pip install -r requirements.txt
python -m ipykernel install --user --name tech-challenge
jupyter notebook notebooks/01_analise_e_modelagem.ipynb
```

### Parte EXTRA — Pneumonia (CNN / visão computacional)

O notebook `Pneumonia.ipynb` foi desenvolvido para **Google Colab** (usa GPU e download via Kaggle). Para executar:

**Opção A — Google Colab (recomendado)**

1. Abra o notebook no Colab ou faça upload de `notebooks/Pneumonia.ipynb`
2. Ative **Runtime → Change runtime type → GPU**
3. Crie uma API key em [kaggle.com/settings](https://www.kaggle.com/settings) e baixe o `kaggle.json`
4. Execute as células na ordem — a célula inicial pede upload do `kaggle.json`
5. O dataset Chest X-Ray será baixado automaticamente (~1,2 GB)

**Opção B — Local (Jupyter)**

```bash
pip install tensorflow opencv-python kaggle jupyter
# Coloque kaggle.json em ~/.kaggle/ (Linux/Mac) ou C:\Users\<user>\.kaggle\ (Windows)
jupyter notebook notebooks/Pneumonia.ipynb
```

> Ajuste `BASE_DIR` nas células de carregamento para o caminho local do dataset após o download manual:
> [Chest X-Ray Pneumonia (Kaggle)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)

### Regenerar relatório (PDF)

```bash
pip install reportlab
python docs/gerar_relatorio.py
```

## Entregáveis (checklist do PDF)

- [x] Repositório Git com código e README
- [x] Notebook ou scripts Python documentados
- [x] Relatório PDF (EDA, pré-processamento, modelos, resultados, discussão crítica)
- [x] Vídeo (até 15 min): [YouTube](https://youtu.be/bGNR-eNHyKk)
- [x] **EXTRA:** CNN em imagens médicas — `Pneumonia.ipynb` (visão computacional)

## Dataset

**Obrigatório:** `data/data.csv` (569 amostras, 30 features + `diagnosis`).

**EXTRA:** Chest X-Ray Pneumonia — download via Kaggle no notebook `Pneumonia.ipynb`.

Se o `data.csv` não existir, o notebook 01 baixa automaticamente da URL do GitHub acima.
