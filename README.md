# Tech Challenge — Fase 1 (IADT)

Projeto de Machine Learning para **classificação de risco/diagnóstico** em contexto de **saúde da mulher**, conforme enunciado da FIAP.

## Problema abordado

Classificar tumores de mama como **malignos** ou **benignos** com base em características numéricas de núcleos celulares (Wisconsin Breast Cancer).

**Fonte dos dados:** [data.csv no repositório SamirGoes/tech_challenge_1](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data/data)

| Coluna | Significado |
|--------|-------------|
| `diagnosis` | `M` = maligno, `B` = benigno |
| demais colunas | 30 medidas numéricas (raio, textura, perímetro, etc.) |


## Estrutura

```
Tech Challenge/
├── data/
│   └── data.csv                       # dataset do tech challenge
├── notebooks/
│   └── 01_analise_e_modelagem.ipynb   # EDA, pré-processamento, modelos, métricas, SHAP
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

```bash
cd "Tech Challenge"
python -m pip install -r requirements.txt
python -m ipykernel install --user --name tech-challenge
jupyter notebook notebooks/01_analise_e_modelagem.ipynb
```

## Entregáveis (checklist do PDF)

- [ ] Repositório Git com código e README
- [ ] Notebook ou scripts Python documentados
- [ ] Relatório PDF (EDA, pré-processamento, modelos, resultados, discussão crítica)
- [ ] Vídeo (até 15 min) no YouTube/Vimeo
- [ ] (Opcional) CNN em mamografias — nota extra

## Dataset

Arquivo local: `data/data.csv` (569 amostras, 30 features + `diagnosis`).

Se o arquivo não existir, o notebook baixa automaticamente da URL do GitHub acima.
