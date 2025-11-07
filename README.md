# USF Tempo de Cuidar - Monitor de Tempo de Agendamento

Sistema de monitorização da carta de direitos do utente do SNS (Serviço Nacional de Saúde) para acompanhamento dos tempos de espera para agendamento de consultas médicas e de enfermagem.

## Descrição do Projeto

Este projeto é um sistema de monitorização desenvolvido para a **USF Tempo de Cuidar** que permite visualizar e acompanhar os tempos de espera para agendamento de consultas. O sistema gera gráficos interativos que mostram a variação dos tempos de espera entre a primeira e segunda vaga de agendamento.

### Funcionalidades

- 📊 **Visualização de Dados**: Gráficos de barras interativos usando Chart.js
- 👨‍⚕️ **Monitorização Médica**: Acompanhamento dos tempos de espera para consultas médicas
- 👩‍⚕️ **Monitorização de Enfermagem**: Acompanhamento dos tempos de espera para consultas de enfermagem
- 📈 **Comparação de Vagas**: Visualização da diferença entre primeira e segunda vaga
- 🎨 **Interface Responsiva**: Design adaptável para diferentes dispositivos
- 🇵🇹 **Localização**: Interface em português

## Estrutura do Projeto

```
monitor/
├── _config.yml              # Configuração do Jekyll
├── _data/
│   └── medicos.csv          # Dados dos profissionais e tempos de espera
├── _includes/
│   └── head.html            # Cabeçalho HTML compartilhado
├── _layouts/
│   └── default.html         # Layout padrão das páginas
├── css/                     # Arquivos de estilo CSS
├── img/                     # Imagens e recursos visuais
├── medicos.html             # Página de monitorização médica
├── enfermeagem.html         # Página de monitorização de enfermagem
├── 404.html                 # Página de erro 404
├── Gemfile                  # Dependências Ruby
└── README.md                # Este arquivo
```

## Pré-requisitos

- **Ruby** (versão 2.7 ou superior)
- **Bundler** (gerenciador de gems do Ruby)
- **Git** (para clonar o repositório)

### Instalação das Dependências no Ubuntu/Debian

```bash
# Instalar Ruby e Bundler
sudo apt update
sudo apt install ruby-full build-essential bundler

# Verificar a instalação
ruby --version
bundler --version
```

### Instalação das Dependências no macOS

```bash
# Usando Homebrew
brew install ruby
gem install bundler

# Verificar a instalação
ruby --version
bundler --version
```

### Instalação das Dependências no Windows

1. Instale o [Ruby Installer](https://rubyinstaller.org/)
2. Durante a instalação, marque a opção "Add Ruby executables to your PATH"
3. Abra o Command Prompt e instale o Bundler:
```cmd
gem install bundler
```

## Instalação e Configuração

### 1. Clonar o Repositório

```bash
git clone https://github.com/nunogand/monitor.git
cd monitor
```

### 2. Instalar as Dependências

```bash
bundle install
```

Este comando irá instalar todas as dependências listadas no `Gemfile`, incluindo:
- Jekyll (~> 4.3.1)
- minima (~> 2.5)
- jekyll-feed (~> 0.12)
- tzinfo e tzinfo-data (para compatibilidade multiplataforma)

### 3. Estrutura de Dados

Os dados são mantidos no arquivo `_data/medicos.csv` com a seguinte estrutura:

```csv
nome,vaga1,vaga2
Dr Mário,6,18
Drª Martina,6,11
Dr Nuno,4,4
Drª Joana,31,38
Enfª Ana,3,4
Enfª Carmen,3,4
Enfª Cristina,3,3
Enfª Sandra,3,3
```

**Campos:**
- `nome`: Nome do profissional de saúde
- `vaga1`: Tempo de espera (em dias) para a primeira vaga
- `vaga2`: Tempo de espera (em dias) para a segunda vaga

## Como Usar

### 1. Desenvolvimento Local

Para executar o site em modo de desenvolvimento:

```bash
bundle exec jekyll serve
```

O site estará disponível em: `http://localhost:4000`

### 2. Estrutura de Navegação

- **Página Principal Médica**: `http://localhost:4000/medicos.html`
  - Mostra os gráficos de tempo de espera para consultas médicas
  - Compara primeira e segunda vaga de agendamento

- **Página de Enfermagem**: `http://localhost:4000/enfermagem.html`
  - Mostra os gráficos de tempo de espera para consultas de enfermagem
  - Compara primeira e segunda vaga de agendamento

### 3. Atualizar Dados

Para atualizar os dados de monitorização:

1. Edite o arquivo `_data/medicos.csv`
2. Adicione novos profissionais ou atualize os tempos de espera
3. Mantenha a estrutura CSV (nome,vaga1,vaga2)
4. O site será automaticamente atualizado na próxima execução

**Exemplo de atualização:**

```csv
nome,vaga1,vaga2
Dr Mário,5,15
Drª Martina,7,12
Dr Nuno,4,4
Drª Joana,28,35
Drª Maria,8,20
Enfª Ana,3,4
Enfª Carmen,3,4
Enfª Cristina,3,3
Enfª Sandra,3,3
Enfª Luísa,2,5
```

### 4. Construir para Produção

Para gerar os arquivos estáticos para deploy:

```bash
bundle exec jekyll build
```

Os arquivos gerados estarão na pasta `_site/`.

## Configuração Avançada

### Personalizar o _config.yml

O arquivo `_config.yml` contém as configurações principais do site:

```yaml
title: USF Tempo de Cuidar - Monitorização
email: nunogand@gmail.com
description: Monitorização da carta de direitos do utente do SNS
url: "https://monitor.usftempodecuidar.pt"
```

**Principais configurações:**
- `title`: Título do site
- `email`: Email do administrador
- `description`: Descrição do projeto
- `url`: URL base do site

### Modificar os Gráficos

Os gráficos são gerados usando Chart.js e podem ser personalizados editando os arquivos:
- `medicos.html` (para consultas médicas)
- `enfermagem.html` (para consultas de enfermagem)

**Opções de personalização disponíveis:**
- Cores dos gráficos
- Tipos de visualização (barras horizontais/verticais)
- Títulos e subtítulos
- Legendas
- Escala dos eixos

### Adicionar Novos Profissionais

1. Edite `_data/medicos.csv`
2. Adicione uma nova linha com os dados do profissional
3. **Para médicos**: As primeiras 4 entradas são exibidas na página médica
4. **Para enfermeiros/as**: As entradas a partir da 5ª posição são exibidas na página de enfermagem

## Deploy

### GitHub Pages

1. Faça push do código para um repositório GitHub
2. Ative o GitHub Pages nas configurações do repositório
3. O site será automaticamente publicado

### Servidor Web Tradicional

1. Execute `bundle exec jekyll build`
2. Faça upload do conteúdo da pasta `_site/` para o seu servidor web
3. Configure o servidor para servir arquivos estáticos

### Netlify

1. Conecte o repositório ao Netlify
2. Configure o comando de build: `bundle exec jekyll build`
3. Configure a pasta de publish: `_site/`

## Solução de Problemas

### Erro: "bundler não encontrado"

```bash
gem install bundler
```

### Erro: "jekyll não encontrado"

```bash
bundle install
bundle exec jekyll serve
```

### Os gráficos não aparecem

1. Verifique se o arquivo `_data/medicos.csv` existe e tem a estrutura correta
2. Confirme que o Chart.js está sendo carregado (verifique a linha 17 em `_includes/head.html`)
3. Verifique o console do navegador para erros JavaScript

### Problemas de encoding

Certifique-se de que o arquivo `_data/medicos.csv` está salvo com encoding UTF-8.

## Licença

Este projeto é desenvolvimento interno da USF Tempo de Cuidar para monitorização dos direitos dos utentes do SNS.

## Suporte

Para suporte técnico ou dúvidas sobre o sistema:
- **Email**: nunogand@gmail.com
- **Projeto**: https://github.com/nunogand/monitor

## Changelog

### Versão Atual (2025-05-28)
- Implementação inicial do sistema de monitorização
- Páginas separadas para consultas médicas e de enfermagem
- Visualização de dados com Chart.js
- Sistema de dados baseado em CSV

---

**Desenvolvido para a USF Tempo de Cuidar - Monitorização do Acesso dos Utentes** 🇵🇹