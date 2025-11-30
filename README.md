# Formulário de Inspeção Interna e Externa – v14

Principais ajustes desta versão:

- Scripts separados:
  - `script_interno.js` (formType = 'interno')
  - `script_externo.js` (formType = 'externo')
- Estruturas de dados independentes:
  - `data_structure_interno.js`
  - `data_structure_externo.js`
- Janela **Dados Iniciais** sem campo de assinatura (interno e externo).
- Janela **Anormalidades e observações** simplificada para 4 campos:
  - Descrição 1, Descrição 2, Observação 1, Observação 2.
- Janela **Anormalidades** **não carrega** dados da inspeção anterior.
- Botão **Enviar Relatório Completo**:
  - Pede confirmação antes de enviar.
  - Após sucesso, pergunta se deseja compartilhar o PDF pelo WhatsApp.
- URLs dos WebApps atualizadas.

## URLs configuradas no JavaScript

No `script_interno.js` e `script_externo.js` foram definidas as seguintes constantes:

```js
const SCRIPT_URL_CARREGAR_INTERNA = 'https://script.google.com/macros/s/AKfycbzwbNHEWGZiraZDQWpfzb6qMHUTnSMy_bC6naTppcLn7hWHKnpXxaHBgjwhoB9jtIk3/exec';
const SCRIPT_URL_CARREGAR_EXTERNA = 'https://script.google.com/macros/s/AKfycbyDOJZxDj6fharoN_trihU8FTG3iU1EdBKPf7qozMw8oOY0TsmOkvTzvbKunHxKwkb3/exec';

const SCRIPT_URL_INTERNA  = 'https://script.google.com/macros/s/AKfycbyoQrnk6x_i1QWRSqGWL1E-S0OnuHxC66S0H388wJ9HTZgfp58QG8iBzY5ZNCkjg1K9qg/exec';
const SCRIPT_URL_EXTERNA = 'https://script.google.com/macros/s/AKfycbxwhnPN5Yr5End7vT8tXtwTE1AOH0gmIFC2okh7qWUcewreWYe5p1qgg7vCR2KnIySA/exec';
```

## Observações 1 e 2 (planilha Externa)

Na aba **Externa**:

- `descricao_1` e `descricao_2` ⇒ **Descrição Anomalia 1 e 2**.
- Colunas **HK** e **HL** (cabeçalhos *Observação 1* e *Observação 2*) devem ser lidas/escritas como:
  - `observacao_1`
  - `observacao_2`

O **Carregar_EXTERNA** (Apps Script) deve mapear essas colunas para estes nomes ao montar o objeto JSON.

## Texto do WhatsApp

Após o envio bem-sucedido, o texto montado é:

```text
Relatório de inspeção INTERNA/EXTERNA – {data}
Operador: {operador}
Supervisor: {supervisor}
Turma: {turma}
Turno: {turno}

PDF:
{pdfUrl}
```

Se o usuário confirmar, será aberto:

```text
https://wa.me/?text=<texto codificado>
```

Sem custo adicional, usando apenas o link público do PDF gerado no Google Drive.

