# Casos de Uso — ChamadoJá

## UC001 — Cadastrar usuário

**Ator:** Administrador

**Objetivo:** Cadastrar um novo usuário no sistema.

**Fluxo principal:**

1. O administrador envia os dados do usuário.
2. O sistema valida os dados informados.
3. O sistema verifica se o e-mail ainda não está cadastrado.
4. O sistema armazena o usuário.
5. O sistema retorna os dados públicos do usuário cadastrado.

**Resultado esperado:** Usuário cadastrado com sucesso.

---

## UC002 — Cadastrar categoria

**Ator:** Administrador

**Objetivo:** Cadastrar uma nova categoria de chamados.

**Fluxo principal:**

1. O administrador informa o nome da categoria.
2. O sistema valida os dados.
3. O sistema verifica se não existe outra categoria com o mesmo nome.
4. O sistema registra a categoria.

**Resultado esperado:** Categoria cadastrada e disponível para utilização nos chamados.

---

## UC003 — Abrir chamado

**Ator:** Solicitante

**Objetivo:** Registrar uma nova solicitação de suporte.

**Fluxo principal:**

1. O solicitante informa a categoria, título, descrição e prioridade.
2. O sistema valida os dados.
3. O sistema verifica se o usuário e a categoria existem.
4. O sistema cria o chamado.
5. O sistema define o status inicial como `aberto`.
6. O sistema retorna os dados do chamado.

**Resultado esperado:** Chamado registrado com status `aberto`.

---

## UC004 — Consultar chamados

**Ator:** Solicitante, Atendente ou Administrador

**Objetivo:** Consultar chamados registrados no sistema.

**Fluxo principal:**

1. O usuário solicita a consulta.
2. O sistema busca os chamados disponíveis.
3. O sistema retorna os dados necessários dos chamados.
4. Quando solicitado, o sistema disponibiliza informações relacionadas, como comentários e histórico.

**Resultado esperado:** Chamados consultados com as informações permitidas.

---

## UC005 — Filtrar e paginar chamados

**Ator:** Solicitante, Atendente ou Administrador

**Objetivo:** Localizar chamados utilizando filtros e paginação.

**Fluxo principal:**

1. O usuário informa um ou mais filtros.
2. O sistema valida os valores informados.
3. O sistema realiza a consulta utilizando os filtros.
4. O sistema aplica a paginação.
5. O sistema retorna os resultados e as informações de navegação.

**Filtros previstos:**

* status;
* prioridade;
* categoria.

**Resultado esperado:** Lista de chamados filtrada e paginada.

---

## UC006 — Atualizar chamado

**Ator:** Atendente ou Administrador

**Objetivo:** Atualizar informações de um chamado existente.

**Fluxo principal:**

1. O usuário informa o identificador do chamado.
2. O sistema verifica se o chamado existe.
3. O usuário informa os dados que deseja atualizar.
4. O sistema valida os dados.
5. O sistema atualiza o chamado.
6. O sistema mantém o identificador e os relacionamentos existentes.

**Resultado esperado:** Chamado atualizado com sucesso.

---

## UC007 — Alterar status e registrar histórico

**Ator:** Atendente ou Administrador

**Objetivo:** Alterar o status de um chamado e registrar sua evolução.

**Fluxo principal:**

1. O usuário informa o chamado e o novo status.
2. O sistema verifica se o chamado existe.
3. O sistema valida o novo status.
4. O sistema verifica se o novo status é diferente do atual.
5. O sistema altera o status.
6. O sistema registra o status anterior, o novo status, o usuário responsável e a data e hora.
7. O sistema retorna o chamado atualizado.

**Resultado esperado:** Status atualizado e alteração registrada no histórico.

---

## UC008 — Registrar comentário

**Ator:** Solicitante, Atendente ou Administrador

**Objetivo:** Adicionar uma informação ou observação a um chamado.

**Fluxo principal:**

1. O usuário informa o chamado e o conteúdo do comentário.
2. O sistema verifica se o chamado existe.
3. O sistema valida o conteúdo.
4. O sistema registra o comentário relacionado ao chamado e ao usuário.
5. O sistema retorna o comentário registrado.

**Resultado esperado:** Comentário associado corretamente ao chamado.

---

## UC009 — Consultar resumo quantitativo

**Ator:** Administrador

**Objetivo:** Obter informações quantitativas sobre os chamados registrados.

**Fluxo principal:**

1. O administrador solicita o resumo.
2. O sistema consulta os chamados registrados.
3. O sistema calcula o total de chamados.
4. O sistema contabiliza os chamados por status.
5. O sistema contabiliza os chamados por prioridade.
6. O sistema contabiliza os chamados por categoria.
7. O sistema retorna o resumo.

**Resultado esperado:** Resumo quantitativo atualizado conforme os dados existentes no sistema.
