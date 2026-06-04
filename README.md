# 🛠️ AutoFix - Sistema de Gestão para Oficina Mecânica

O **AutoFix** é uma solução digital ponta a ponta projetada para otimizar, automatizar e gerenciar os fluxos operacionais de uma oficina mecânica. O sistema unifica desde o cadastro inicial de clientes e veículos até a emissão de orçamentos complexos e faturamento financeiro.

---

## 🎯 Objetivo e Contexto

O AutoFix foi desenvolvido no contexto acadêmico como parte da disciplina de Projeto de Software. O objetivo principal do projeto é mitigar falhas humanas, atrasos e falta de controle decorrentes do uso de processos analógicos (como papel e planilhas) em oficinas de manutenção automotiva.

O sistema soluciona dores críticas do negócio, tais como:
* **Falta de rastreabilidade:** Controle em tempo real de peças utilizadas e nível do estoque.
* **Gargalos operacionais:** Visibilidade do diagnóstico de Ordens de Serviço (OS) pelos mecânicos.
* **Ruídos de comunicação:** Transparência na aprovação de orçamentos junto aos clientes.

Trata-se de um ambiente experimental e simulado focado em cenários reais de pequenas e médias oficinas mecânicas que buscam transição digital e maior controle de sua margem de lucro.

---

## 🏗️ Visão Geral da Arquitetura e Engenharia

A arquitetura do AutoFix foi planejada utilizando práticas consolidadas de mercado para garantir a separação de responsabilidades, manutenibilidade e escalabilidade do software. O projeto segue os padrões **UML** e o **C4 Model** (Nível 2 - Contêineres), estruturando-se da seguinte forma:

1. **Front-end (SPA):** Desenvolvido em **React com TypeScript**, fornecendo uma interface de usuário rica, dinâmica e responsiva adaptada para os perfis de Recepcionista, Mecânico e Gerente.
2. **Back-end (API REST):** Construído em **Node.js** seguindo o padrão de arquitetura em camadas *Boundary-Control-Entity (BCE)* (separação clara entre Controllers, Services e Repositories).
3. **Persistência (Banco de Dados):** Banco de dados relacional **PostgreSQL**, modelado com chaves estrangeiras estruturadas e mapeado na aplicação por meio de um ORM (Object-Relational Mapping) sobre as tabelas `tb_cliente`, `tb_veiculo`, `tb_ordem_servico`, `tb_item_os`, `tb_servico` e `tb_peca`.
4. **Infraestrutura:** Orquestração de serviços e isolamento de ambientes locais utilizando contêineres **Docker**.

---

## 🚀 Tecnologias Utilizadas

* **Front-end:** [React](https://react.dev/), TypeScript, Vite, TailwindCSS.
* **Back-end:** [Node.js](https://nodejs.org/), Express / NestJS, TypeORM (Mapeamento Objeto-Relacional).
* **Banco de Dados:** [PostgreSQL](https://www.postgresql.org/).
* **DevOps / Infra:** [Docker](https://www.docker.com/) & Docker Compose.
* **Modelagem Técnica:** PlantUML (C4 Model, Diagramas de Classes, Comunicação, Sequência e Estados).

---

## 💻 Pré-requisitos de Ambiente

Antes de iniciar a execução da aplicação, certifique-se de ter instalado em sua máquina:

* **Node.js:** Versão LTS (v18.x ou superior).
* **Gerenciador de Pacotes:** `npm` ou `yarn`.
* **Docker & Docker Compose:** Obrigatório para subir a instância isolada do banco de dados PostgreSQL sem a necessidade de configurações locais complexas.

---

## ⚙️ Como Executar o Projeto (Desenvolvimento)

Siga os passos abaixo para clonar o repositório e rodar o ecossistema localmente em sua máquina de desenvolvimento:

### 1. Clonar o Repositório
```bash
git clone [https://github.com/seu-usuario/autofix.git](https://github.com/seu-usuario/autofix.git)
cd autofix
```
### 2. Inicializar o Banco de Dados (Docker)

Na raiz do projeto (onde se encontra o arquivo docker-compose.yml), execute o comando para iniciar o contêiner do PostgreSQL em segundo plano:
```bash
docker-compose up -d
```
### 3. Configurar e Executar o Back-end
```bash
cd backend
npm install
# Certifique-se de configurar as variáveis no arquivo .env se necessário
npm run start:dev
```
### 4. Configurar e Executar o Front-end
Abra um novo terminal na raiz do projeto e execute:

```bash
cd frontend
npm install
npm run dev
```
Após a inicialização, acesse a aplicação no seu navegador através do endereço local indicado no terminal (geralmente http://localhost:5173).

## 📦 Instruções de Build e Deploy
Para gerar os artefatos de produção otimizados e prontos para distribuição, utilize os comandos listados a seguir:

### 1. Build do Front-end (React)
Gera arquivos estáticos otimizados (HTML, CSS compactados e minificados) na pasta /dist:

```bash
cd frontend
npm run build
```
### 2. Build do Back-end (Node.js)
Compila o código TypeScript em JavaScript puro interpretável diretamente pelo Node.js na pasta de saída (geralmente /dist ou /build):

```bash
cd ../backend
npm run build
```
### 3. Configuração do Ambiente de Produção
Ao realizar o deploy em provedores de nuvem (como Render, AWS, Railway ou Google Cloud), certifique-se de definir corretamente as seguintes variáveis de ambiente:

DATABASE_URL: String de conexão segura com a instância do banco de dados PostgreSQL de produção.

VITE_API_URL: URL pública da API do back-end para que o cliente front-end consiga realizar as requisições HTTP corretamente.

## 🤝 Guia para Contribuições
Contribuições, correções ou sugestões de melhoria na modelagem e na arquitetura são muito bem-vindas!

* Faça um fork do projeto.

* Crie uma branch específica para sua funcionalidade (git checkout -b feature/minha-feature).

* Adicione suas alterações e faça o commit utilizando o padrão de Conventional Commits (git commit -m 'feat: Adiciona funcionalidade X').

* Envie a branch para o seu repositório remoto (git push origin feature/minha-feature).

* Abra um Pull Request (PR) detalhando as mudanças realizadas para revisão.
