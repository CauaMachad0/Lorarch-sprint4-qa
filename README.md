# LorArch — Sprint 4 · Compliance, Quality Assurance & Tests

**Data:** 2025-11-07  
**Equipe:**  
- Cauã Marcelo da Silva Machado — RM 558024  
- Gabriel Lima Silva — RM 556773  
- Marcos Ramalho — RM 554611  

---

## 📌 Escopo da Entrega
Validação de qualidade do sistema **LorArch** focada na **API Java + Interface Web**. Inclui:
- **Parte A (manuais):** plano de testes com entradas, saídas e passos
- **Parte B (automatizados):** collection Postman com ≥ 4 casos + vídeo de execução

---

## 🗂 Estrutura deste repositório
```
/
├─ docs/
│  └─ Plano_de_Testes_LorArch_Sprint4_Completo.docx
├─ tests/
│  └─ postman/
│     ├─ LorArch_Sprint4_Postman_Collection.json
│     └─ LorArch_Localhost.postman_environment.json
├─ evidence/
└─ .gitignore
```

> **Observação:** se sua API estiver publicada no Azure, ajuste a variável `{baseUrl}` no Postman Environment.

---

## ▶️ Como rodar a API local (Java/Spring Boot)
```bash
# 1) Ajuste application.properties/yml com URL do banco (Oracle) ou H2 para DEV
# 2) Rode a aplicação
./gradlew bootRun
# ou
mvn spring-boot:run
```

Endpoints úteis:
- `GET /swagger-ui.html`
- `GET /v3/api-docs`
- `GET /actuator/health`

---

## 🤖 Testes Automatizados (Postman)
## 🤖 Testes Automatizados (Postman)

1. Abra o **Postman** → **Import** → selecione os arquivos de `tests/postman/`  
2. Selecione o **Environment** `LorArch - Localhost`  
3. Garanta que a API esteja rodando no `{baseUrl}` configurado no Environment  
4. Execute a **Collection** pelo **Runner**, seguindo a ordem sugerida abaixo:

---

### 🏍️ Motos
| Método | Endpoint | Descrição |
|:------:|:----------|:-----------|
| **POST** | `/motos` | Criar nova moto |
| **GET** | `/motos` | Listar todas as motos |
| **GET** | `/motos/{motoId}` | Detalhar moto específica |
| **PUT** | `/motos/{motoId}` | Atualizar dados da moto |
| **PATCH** | `/motos/{motoId}/status` | Alterar status *(ex.: enviar para manutenção)* |
| **DELETE** | `/motos/{motoId}` | Excluir moto |

---

### ⚙️ Ocorrências
| Método | Endpoint | Descrição |
|:------:|:----------|:-----------|
| **POST** | `/ocorrencias` | Criar nova ocorrência |
| **GET** | `/ocorrencias` | Listar todas as ocorrências |
| **GET** | `/ocorrencias/{ocorrenciaId}` | Detalhar ocorrência específica |
| **PUT** | `/ocorrencias/{ocorrenciaId}` | Atualizar dados da ocorrência |
| **PATCH** | `/ocorrencias/{ocorrenciaId}/status` | Alterar status *(ex.: fechamento ou manutenção)* |
| **DELETE** | `/ocorrencias/{ocorrenciaId}` | Excluir ocorrência |

---

> ✅ A collection já valida **status codes**, **estrutura JSON** e **persistência dos dados**.


### Executar via Newman (CLI)
```bash
npm i -g newman
newman run tests/postman/LorArch_Sprint4_Postman_Collection.json \
  -e tests/postman/LorArch_Localhost.postman_environment.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export evidence/newman-report.html

```
O relatório HTML será salvo em `evidence/newman-report.html`.

---

## 🧪 Testes Manuais

**Plano completo com casos (entradas, saídas e passos):**  
`docs/Plano_de_Testes_LorArch_Sprint4_Completo.docx`

**Abrange:**
- CRUD de **Motos** e **Ocorrências**
- **Envio** e **conclusão de manutenção** *(com geração automática de ocorrência)*
- **Validações de formulário** (Thymeleaf) e mensagens de erro
- Conferência do **dashboard** (Resumo da Frota)

---

## 🔗 Links de Entrega

Preencha antes de enviar:
- **Azure Boards (item Sprint 4):** <https://dev.azure.com/lorarch/LorArch/_workitems/edit/138>  
- **Vídeo de execução:** <https://www.youtube.com/watch?v=meP73Uc6n9c>

---

## ✅ Status

- ✅ Collection e Environment **incluídos**
- ✅ Plano de Testes **anexado**
- ✅ Evidências (prints/vídeo/relatório) em `evidence/`
- ✅ Testes **aprovados** nas rotas de **Motos** e **Ocorrências**
