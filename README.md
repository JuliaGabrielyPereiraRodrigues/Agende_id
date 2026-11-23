
<div align="center">

# 📅 AgendeID

### Sistema Inteligente de Agendamento de Serviços

**Plataforma web para agendamento de serviços de emissão da Carteira de Identidade, com atendimento automatizado por chatbot e Inteligência Artificial.**

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

<br>

[Sobre](#-sobre-o-projeto) •
[Funcionalidades](#-funcionalidades) •
[Tecnologias](#-tecnologias-utilizadas) •
[Instalação](#-instalação-e-execução) •
[Estrutura](#-estrutura-do-projeto)

</div>

---

## 📖 Sobre o projeto

O **AgendeID** é uma aplicação web desenvolvida para simular e otimizar o processo de agendamento de serviços relacionados à emissão da Carteira de Identidade.

O sistema integra **desenvolvimento web, banco de dados e Inteligência Artificial**, oferecendo atendimento automatizado por meio de um chatbot capaz de identificar intenções dos usuários e auxiliar na realização de diferentes operações.

A solução foi desenvolvida como projeto acadêmico, explorando conceitos de arquitetura de software, autenticação, persistência de dados e Processamento de Linguagem Natural (PLN).

### 🎯 Objetivos

- Facilitar o acesso aos serviços de agendamento.
- Automatizar etapas do atendimento ao usuário.
- Centralizar informações de clientes e agendamentos.
- Oferecer funcionalidades específicas para clientes e funcionários.
- Explorar a aplicação de Inteligência Artificial em sistemas web.

---

## ✨ Funcionalidades

### 👤 Área do cliente

O sistema possui funcionalidades voltadas ao gerenciamento de atendimentos pelos usuários.

- Cadastro de novos usuários.
- Autenticação e gerenciamento de sessões.
- Agendamento de serviços.
- Consulta de agendamentos existentes.
- Alteração de data e horário.
- Cancelamento de agendamentos.
- Consulta de horários disponíveis.
- Interação com o assistente virtual.

### 👨‍💼 Área do funcionário

O projeto também apresenta funcionalidades administrativas para gerenciamento dos atendimentos.

- Visualização da agenda de atendimentos.
- Consulta de informações de clientes.
- Busca de clientes por identificadores.
- Confirmação de presença.
- Acompanhamento de agendamentos.
- Geração de relatórios de comparecimento e serviços.

### 🤖 Assistente virtual

O chatbot foi desenvolvido para auxiliar na interação entre usuários e sistema.

Entre os recursos implementados estão:

- Identificação de intenções em mensagens.
- Processamento de entradas em linguagem natural.
- Respostas automatizadas.
- Reconhecimento de solicitações relacionadas a agendamentos.
- Gerenciamento do contexto de conversação.
- Integração com operações de consulta e atualização de dados.

> **Observação:** as funcionalidades acima estão representadas no código-fonte. O projeto possui pontos de integração e configuração que podem exigir ajustes para funcionamento completo.

---

## 🛠️ Tecnologias utilizadas

### Back-end

| Tecnologia | Finalidade |
|:---|:---|
| **Python** | Linguagem principal da aplicação |
| **Flask** | Desenvolvimento do servidor e das rotas HTTP |
| **SQLite** | Armazenamento de usuários e agendamentos |
| **Flask-CORS** | Configuração de requisições entre origens |
| **Flask-WTF** | Recursos de proteção CSRF |
| **Flask-Limiter** | Limitação de requisições |

### Front-end

| Tecnologia | Finalidade |
|:---|:---|
| **HTML5** | Estrutura das interfaces |
| **CSS3** | Estilização dos componentes |
| **JavaScript** | Interatividade e comunicação com o servidor |
| **Bootstrap** | Componentes e estilização responsiva |
| **Fetch API** | Requisições assíncronas às rotas da aplicação |

### Inteligência Artificial

| Tecnologia | Finalidade |
|:---|:---|
| **TensorFlow / Keras** | Construção e execução da rede neural |
| **NLTK** | Tokenização e processamento de linguagem natural |
| **NumPy** | Manipulação de vetores e dados numéricos |
| **JSON** | Definição das intenções e respostas do chatbot |

---

## 🧠 Inteligência Artificial e Chatbot

O AgendeID utiliza um modelo de classificação de intenções baseado em rede neural, desenvolvido com **TensorFlow e Keras**.

O treinamento utiliza exemplos de mensagens organizados no arquivo `intents.json`.

### Como funciona?

O processamento das mensagens segue as seguintes etapas:

1. **Entrada:** o usuário envia uma mensagem pela interface.
2. **Pré-processamento:** o texto passa por tokenização e normalização.
3. **Representação:** as palavras são convertidas em vetores de características.
4. **Classificação:** a rede neural identifica a intenção mais provável.
5. **Processamento:** o chatbot seleciona a resposta ou executa a lógica correspondente.
6. **Resposta:** o sistema retorna o resultado ao usuário.

### Arquitetura da rede neural

O script de treinamento define uma rede neural sequencial com:

- Camada densa de 128 neurônios e ativação ReLU.
- Camada Dropout de 50%.
- Camada densa de 64 neurônios e ativação ReLU.
- Segunda camada Dropout de 50%.
- Camada de saída com ativação Softmax.

O modelo utiliza a função de perda `categorical_crossentropy` e um otimizador SGD com momentum.

O treinamento está configurado com **200 épocas** e lotes de 5 exemplos.

### Arquivos produzidos pelo treinamento

```text
backend/
└── modelos_salvos/
    ├── chatbot_model.h5
    ├── words.pkl
    └── classes.pkl
```

Esses arquivos armazenam o modelo treinado, o vocabulário e as classes reconhecidas.

---

## 🏗️ Arquitetura do sistema

A aplicação utiliza uma arquitetura web com separação entre interfaces, regras de negócio e persistência de dados.

```text
                 ┌──────────────────────┐
                 │       USUÁRIO        │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │      FRONT-END       │
                 │ HTML • CSS • JS      │
                 └──────────┬───────────┘
                            │ HTTP
                            ▼
                 ┌──────────────────────┐
                 │      FLASK API       │
                 │ Rotas e autenticação │
                 └──────────┬───────────┘
                            │
                ┌───────────┴───────────┐
                │                       │
                ▼                       ▼
     ┌───────────────────┐   ┌───────────────────┐
     │      CHATBOT      │   │    BANCO DE DADOS │
     │ TensorFlow / NLTK │   │       SQLite      │
     └───────────────────┘   └───────────────────┘
```

O Flask é responsável por receber requisições, gerenciar sessões, renderizar as páginas e integrar as funcionalidades do chatbot com o banco de dados.

---

## 📁 Estrutura do projeto

```text
Agende_id/
│
├── AgendeID_FINAL/
│   │
│   ├── backend/
│   │   ├── chatbot.py
│   │   ├── chatbot_model_treino.py
│   │   └── database.py
│   │
│   ├── static/
│   │   ├── script.js
│   │   ├── script_cliente.js
│   │   ├── script_funcionario.js
│   │   └── style.css
│   │
│   ├── templates/
│   │   ├── index.html
│   │   ├── painel_cliente.html
│   │   └── painel_funcionario.html
│   │
│   ├── app.py
│   ├── banco.db
│   ├── intents.json
│   ├── requirements.txt
│   └── README.txt
│
└── README.md
```

### Principais componentes

- **`app.py`:** inicialização do servidor Flask, rotas e gerenciamento de sessões.
- **`chatbot.py`:** processamento das mensagens e implementação das regras de conversação.
- **`chatbot_model_treino.py`:** treinamento da rede neural para classificação de intenções.
- **`database.py`:** conexão e operações no banco de dados SQLite.
- **`intents.json`:** conjunto de intenções utilizado pelo chatbot.
- **`templates/`:** páginas HTML da aplicação.
- **`static/`:** arquivos de estilo e scripts de interação.

---

## 🚀 Instalação e execução

### Pré-requisitos

Para executar o projeto localmente, é necessário possuir:

- Python instalado.
- pip para gerenciamento de dependências.
- Git para clonar o repositório.
- Ambiente compatível com as dependências do TensorFlow.

> O projeto utiliza TensorFlow 2.15.0. Recomenda-se um ambiente Python 3.10 para maior compatibilidade com as dependências declaradas.

### 1. Clone o repositório

```bash
git clone https://github.com/JuliaGabrielyPereiraRodrigues/Agende_id.git
```

Acesse a pasta principal da aplicação:

```bash
cd Agende_id/AgendeID_FINAL
```

### 2. Crie um ambiente virtual

```bash
python -m venv venv
```

Ative o ambiente virtual.

**Windows:**

```powershell
.\venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

### 3. Instale as dependências

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

> Caso a instalação apresente problemas de leitura, verifique a codificação do `requirements.txt`. O arquivo fornecido está salvo em UTF-16 e pode precisar ser convertido para UTF-8.

### 4. Treine o modelo de Inteligência Artificial

Execute:

```bash
python backend/chatbot_model_treino.py
```

O script realiza o pré-processamento das intenções, treina a rede neural e salva os arquivos do modelo no diretório `backend/modelos_salvos/`.

### 5. Configure as variáveis de ambiente

Crie um arquivo `.env` na pasta `AgendeID_FINAL`:

```env
FLASK_SECRET_KEY=substitua-por-uma-chave-secreta-forte
```

A chave deve ser mantida em segredo e não deve ser enviada ao GitHub.

### 6. Inicie o servidor

```bash
python app.py
```

A aplicação está configurada para utilizar a porta `5000`.

Acesse no navegador:

**http://localhost:5000**

> **Atenção:** os comandos representam o fluxo previsto pelo projeto. A execução completa não foi validada neste ambiente. O uso de cookies seguros, as configurações de CSRF e alguns pontos das rotas podem exigir ajustes para testes locais.

---

## 🔐 Segurança e gerenciamento de dados

O código inclui recursos relacionados à segurança da aplicação, como:

- Armazenamento de senhas utilizando funções de hash.
- Sessões de autenticação.
- Separação de acesso entre clientes e funcionários.
- Configuração de proteção CSRF.
- Limitação de requisições.
- Cabeçalhos de segurança HTTP.
- Validações de dados de cadastro.

Esses mecanismos fazem parte da implementação acadêmica e **não representam uma auditoria de segurança ou garantia de prontidão para produção**.

---

## 📚 Aprendizados

O desenvolvimento do AgendeID envolve a aplicação prática de conhecimentos em:

- Desenvolvimento web full stack.
- Construção de APIs com Flask.
- Integração entre front-end e back-end.
- Modelagem e manipulação de bancos de dados.
- Gerenciamento de autenticação e sessões.
- Processamento de Linguagem Natural.
- Treinamento de redes neurais.
- Organização de aplicações Python.

---

## 🔮 Possíveis melhorias

Como oportunidades de evolução do projeto, destacam-se:

- Implementação de testes automatizados.
- Aprimoramento da validação de formulários.
- Revisão das configurações de segurança para produção.
- Melhoria da organização das dependências.
- Ampliação do conjunto de treinamento do chatbot.
- Adição de métricas de avaliação do modelo.
- Implantação da aplicação em ambiente de hospedagem.
- Aprimoramento da interface responsiva.

---

## 📌 Natureza do projeto

O **AgendeID** foi desenvolvido com finalidade acadêmica, como demonstração da integração entre desenvolvimento web, banco de dados e Inteligência Artificial.

A aplicação simula um sistema de agendamento de serviços de identificação civil, não representando um serviço oficial de emissão de documentos.

---

## 👩‍💻 Autoria

Desenvolvido por **[Julia Gabriely](https://github.com/JuliaGabrielyPereiraRodrigues)**.

<div align="center">

---

**[⬆ Voltar ao topo](#-agendeid)**

</div>
