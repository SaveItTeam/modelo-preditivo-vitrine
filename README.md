# 🧠 Modelo Preditivo

Este projeto automatiza o processo de **selecionar o melhor modelo de Machine Learning** com base na métrica de desempenho escolhida — `accuracy` (para classificação) ou `r2` (para regressão).  

A ferramenta recebe um **DataFrame**, realiza o pré-processamento, treina múltiplos modelos, avalia os resultados e **salva automaticamente o melhor modelo** como `best_model.pkl`.

---

## 🚀 Funcionalidades

- 🔍 Detecção automática de tipo de problema (classificação ou regressão)
- 🧩 Treinamento e avaliação de múltiplos algoritmos
- 🏆 Seleção automática do modelo com melhor desempenho
- 📊 Exibição de métricas (Acurácia, R², Matriz de confusão, Relatório de classificação)
- 💾 Exportação automática do melhor modelo em `.pkl`
- ⚙️ CI/CD com **GitHub Actions**, validando e publicando o modelo automaticamente

---

## 🧰 Tecnologias

- Python 3.10+
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook
- GitHub Actions (CI/CD)

---

## 🧩 Estrutura do Projeto

```
modelo-preditivo-vitrine/
│
├── main.ipynb                # Notebook principal que treina e avalia os modelos
├── requirements.txt          # Dependências do projeto
├── best_model.pkl            # (Gerado após execução) Modelo com melhor desempenho
│
├── .github/
│   └── workflows/
│       └── pipeline.yml      # Pipeline CI/CD (executa notebook e publica modelo)
│
└── README.md                 # Documentação do projeto
```

---

## ⚙️ Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/SaveItTeam/modelo-preditivo-vitrine.git
   cd modelo-preditivo-vitrine
   ```

2. Crie um ambiente virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux/macOS
   venv\Scripts\activate      # Windows
   ```

3. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

---

## 🧪 Como Usar

1. Abra o notebook principal:
   ```bash
   jupyter notebook main.ipynb
   ```

2. Carregue seu dataset (por exemplo, `data.csv` com a coluna `target`).

3. Escolha a métrica:
   - `'accuracy'` → problema de **classificação**
   - `'r2'` → problema de **regressão**

4. O script treinará diferentes modelos, exibirá o desempenho e **salvará automaticamente o melhor modelo** em:
   ```
   best_model.pkl
   ```

5. Para fazer previsões depois:
   ```python
   import pickle
   model = pickle.load(open("best_model.pkl", "rb"))
   y_pred = model.predict(X_novos_dados)
   ```

---

## 🧱 Pipeline CI/CD

O repositório já vem com uma pipeline automatizada configurada em **GitHub Actions** (`.github/workflows/pipeline.yml`).

### 🔄 O que ela faz:

1. Instala dependências  
2. Converte o notebook (`main.ipynb`) em script (`main.py`)  
3. Executa o código  
4. Salva `best_model.pkl`  
5. Publica o modelo como artefato para download direto no GitHub  

### 💡 Como funciona:

A cada `push` ou `pull request` na branch `main` ou `develop`, a pipeline é executada automaticamente.

Você pode acompanhar o progresso em:  
**GitHub → Actions → CI/CD - Modelo Preditivo Vitrine**

### 📤 Baixar o modelo treinado

Após a execução da pipeline, vá em:
```
Actions → Run details → Artifacts → best_model.zip
```
e baixe o modelo atualizado.

---

## 🧩 Exemplo de Saída

```
=== Random Forest ===
Acurácia no teste: 0.9275
Matriz de confusão:
[[51  2]
 [ 3 44]]

=== KNN ===
Acurácia no teste: 0.8900
...

🏆 Melhor modelo: Random Forest (accuracy = 0.9275)
Modelo salvo como: best_model.pkl
```

---

## 📦 Próximos Passos

- [ ] Adicionar novos algoritmos (XGBoost, LightGBM)
- [ ] Criar API REST para servir previsões
- [ ] Armazenar modelos em nuvem (AWS S3 / GCP Storage)
- [ ] Monitorar performance com MLflow ou Weights & Biases

---

## 👥 Autores

Projeto desenvolvido por **SaveItTeam**  
com foco em automação e eficiência em Machine Learning.
