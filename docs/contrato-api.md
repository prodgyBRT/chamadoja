# Contrato da API — ChamadoJá

Todas as requisições enviadas e respostas recebidas pela API devem utilizar o formato JSON e incluir os cabeçalhos:
- `Accept: application/json`
- `Content-Type: application/json`


## Mapeamento Geral de Rotas

| Método | Rota | Objetivo / Caso de Uso | Status HTTP |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/usuarios` | UC001 — Cadastrar usuário | `201 Created` |
| `GET` | `/api/usuarios` | RF002 — Consultar usuários | `200 OK` |
| `GET` | `/api/usuarios/{id}` | RF002 — Consultar usuário específico | `200 OK` |
| `POST` | `/api/categorias` | UC002 — Cadastrar categoria | `201 Created` |
| `GET` | `/api/categorias` | RF004 — Consultar categorias | `200 OK` |
| `GET` | `/api/categorias/{id}` | RF004 — Consultar categoria específica | `200 OK` |
| `POST` | `/api/chamados` | UC003 — Abrir chamado | `201 Created` |
| `GET` | `/api/chamados` | UC004/UC005 — Listar, filtrar e paginar chamados | `200 OK` |
| `GET` | `/api/chamados/{id}` | RF006 — Consultar detalhes de um chamado | `200 OK` |
| `PATCH` | `/api/chamados/{id}` | UC006 — Atualizar chamado | `200 OK` |
| `POST` | `/api/chamados/{id}/comentarios` | UC008 — Registrar comentário | `201 Created` |
| `PATCH` | `/api/chamados/{id}/status` | UC007 — Alterar status e gerar histórico | `200 OK` |
| `GET` | `/api/chamados/{id}/historico` | RF012 — Consultar histórico de status | `200 OK` |
| `GET` | `/api/chamados/resumo` | UC009 — Consultar resumo quantitativo | `200 OK` |


## Exemplos Detalhados de Entrada e Saída

### 1. Abrir Chamado (`POST /api/chamados`)
> Conforme **RN004**, todo chamado nasce automaticamente com o status `aberto`[span_4](start_span)[span_4](end_span)[span_5](start_span)[span_5](end_span).

#### Payload de Entrada (Request Body)

{
  "solicitante_id": 1,
  "categoria_id": 2,
  "titulo": "Impressora do setor financeiro não liga",
  "descricao": "A impressora parou de funcionar após o surto de energia de ontem.",
  "prioridade": "alta"
}


Resposta de Sucesso (201 Created)

{
  "id": 10,
  "solicitante_id": 1,
  "categoria_id": 2,
  "titulo": "Impressora do setor financeiro não liga",
  "descricao": "A impressora parou de funcionar após o surto de energia de ontem.",
  "prioridade": "alta",
  "status": "aberto",
  "criado_em": "2026-09-30T10:00:00Z",
  "atualizado_em": "2026-09-30T10:00:00Z"
}

Resposta de Erro de Validação (422 Unprocessable Content) — RF014

{
  "mensagem": "Os dados fornecidos são inválidos.",
  "erros": {
    "categoria_id": [
      "A categoria selecionada não existe no sistema."
    ],
    "prioridade": [
      "O campo prioridade aceita somente: baixa, media, alta, urgente."
    ]
  }
}
## 2. listagem de chamados com filtros e paginação (GET/api/chamados)

conforme RF010 e UC005, a listagem aceita parâmetros na URL

(?status+aberto&prioridade=urgente&pagina=1)
e retorna os dados envolvidos em um envelope com metadados de paginação.

reposta de sucesso (200 ok)

{
    "dados": [
        {
        "id": 10,
        "solicitante_id": 1,
        "categoria_id": 2,
        "titulo": Impressora do setor financeiro nãi liga",
        "status": "aberto",
        "criado_em": "2026-09-30t10:00:00z"
        }
    ]
    "meta": {
        "pagina_atual": 1,
        "total_paginas": 5,
        "por_pagina": 15,
        "total_registros": 72
    }
}

## 3. Alterar Status do Chamado (PATCH /api/chamados/{id}/status)

Conforme RN006 e RN007, altera o status e registra o histórico (status anterior, novo status, responsável e data/hora).

Payload de Entrada

{
  "usuario_id": 2,
  "status": "em_andamento"
}

Resposta de Sucesso (200 OK)

{
  "mensagem": "Status alterado com sucesso.",
  "chamado_id": 10,
  "status_anterior": "aberto",
  "novo_status": "em_andamento",
  "usuario_id": 2,
  "alterado_em": "2026-09-30T10:15:00Z"
}

## 4. Consultar resumo Quantitativo (GET/api/chamados/resumo)

conforme RF013 e UC009, retona métricas consolidadas por status, prioridade e categoria.

Resposta de Sucesso (200 ok)

{
    "total_chamados": 45,
    "por_status": {
        "aberto": 12,
        "em_andamento": 8,
        "aguardando": 5,
        "resolvido": 15,
        "fechado": 5
        },
        "por_prioridade": {
            "baixa": 10,
            "media": 20,
            "alta": 10,
            "urgente": 5
        },
        "por_categoria": {
            "hardware": 18,
            "software": 20,
            "redes": 7
        }
}


## 5. Tratamento de Recurso Inexistente (404 Not Found) — RF015
Exemplo ao buscar ou alterar um chamado que não existe:


{
  "mensagem": "Recurso não encontrado."
}