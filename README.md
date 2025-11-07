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
- Evidências e links solicitados pela FIAP

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
│  └─ (adicione aqui prints da execução dos testes e screenshot do item Done no Boards)
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
1. Abra o **Postman** → **Import** → selecione os arquivos em `tests/postman/`  
2. Selecione o **environment** `LorArch - Localhost`  
3. Garanta que a API está rodando em `{baseUrl}` (ajuste se necessário)  
4. Execute a collection via **Runner** (ordem sugerida):
   - **Auth** → `POST /login`
   - **Motos** → `POST /motos (criar)` → `GET /motos` → `PUT /motos/{motoId}` → `PATCH /motos/{motoId}/status` → `DELETE /motos/{motoId}`
   - **Ocorrencias** → `POST /ocorrencias` → `PUT /ocorrencias/{ocorrenciaId}` → `PATCH /ocorrencias/{ocorrenciaId}/status` → `DELETE /ocorrencias/{ocorrenciaId}`

### Executar via Newman (CLI)
```bash
npm i -g newman
newman run tests/postman/LorArch_Sprint4_Postman_Collection.json   -e tests/postman/LorArch_Localhost.postman_environment.json   --reporters cli,htmlextra --reporter-htmlextra-export evidence/newman-report.html
```
O relatório HTML será salvo em `evidence/newman-report.html`.

---

## 🧪 Testes Manuais
O plano completo com casos (entradas, saídas e passos) está em:  
`docs/Plano_de_Testes_LorArch_Sprint4_Completo.docx`

---

## 🔗 Links de Entrega
Preencha aqui antes de enviar:
- **Azure Boards (item da Sprint 4):** (https://dev.azure.com/lorarch/LorArch/_workitems/edit/138)
- **Vídeo da execução (Postman Runner/Newman):** _cole o link aqui_

