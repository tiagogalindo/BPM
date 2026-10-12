# BPM

## Guia rápido: criando um buscador de obras (BI básico)

Este repositório pode ser usado como ponto de partida para um projeto de
Business Intelligence focado em obras de construção civil. A seguir está um
roteiro recomendado para iniciantes que desejam montar um buscador capaz de
listar obras por construtora ou localizar a construtora responsável por uma
obra específica.

### 1. Definir as fontes de dados

1. Levante onde os dados estão: planilhas, sistemas internos, sites públicos.
2. Padronize campos principais (nome da obra, construtora, cidade, status,
   datas, orçamento, responsável técnico etc.).
3. Escolha um formato inicial simples, como uma planilha CSV, para facilitar a
   importação e limpeza dos dados.

### 2. Modelar e armazenar as informações

* Para começar rápido, utilize uma tabela única em um banco relacional leve
  (SQLite, PostgreSQL) contendo todos os campos necessários.
* Se o volume crescer, evolua para um modelo dimensional (fato/dimensões) para
  melhorar as análises.

### 3. Criar o backend da aplicação

* Implemente uma API REST simples (Node.js/Express, Python/FastAPI, etc.).
* Rotas sugeridas:
  * `GET /construtoras?nome=...` – lista construtoras e suas obras.
  * `GET /obras?nome=...` – busca obras e retorna construtora, status, datas.
* Garanta filtros básicos (cidade, status, período) e paginação para resultados
  grandes.

### 4. Construir a interface de busca

* Comece com um formulário simples em HTML/JavaScript ou use um framework
  (React, Vue, Angular).
* Exiba resultados em tabela com colunas chave (obra, construtora, status,
  início, previsão de entrega, responsável) e botões para detalhes.
* Inclua campos de busca por construtora ou por obra, utilizando a mesma API.

### 5. Adicionar visualizações (BI)

* Crie gráficos básicos (obras por construtora, obras por status, evolução do
  orçamento). Bibliotecas como Chart.js ou Apache ECharts são acessíveis a
  iniciantes.
* Permita exportar relatórios (PDF/Excel) para compartilhamento.

### 6. Segurança e governança de dados

* Controle o acesso ao sistema (login/senha, papéis de usuário).
* Mantenha trilhas de auditoria sobre alterações nos dados.
* Atualize dados periodicamente e monitore a qualidade.

### 7. Próximos passos

* Automatizar ingestão de dados via ETL (Airflow, dbt, scripts Python).
* Integrar com ferramentas de BI prontas (Power BI, Metabase, Superset) para
  dashboards mais completos.
* Evoluir o modelo para suportar indicadores financeiros e de andamento das
  obras.

Com esse roteiro, você terá uma base sólida para criar um buscador de obras e
expandir gradualmente para uma solução de BI mais completa.