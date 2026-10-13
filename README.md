# Entregável de Desenvolvimento Web – Objetos, Dados e Assincronismo – Semana 05

## 💻 Sobre o Projeto
Este projeto consiste no desenvolvimento de um mini projeto de consumo de APIs e manipulação dinâmica do DOM, aplicando conceitos avançados de objetos, arrays, assincronismo (Promises, async/await) e Fetch API. 

A aplicação gerencia de forma robusta os **quatro estados de uma tela**: *Carregando, Erro, Vazio/Não Encontrado e Sucesso*. O projeto é composto pelos arquivos `index.html` e `app.js`.

---

## 🛠️ Conteúdo Estruturado do Projeto

### Parte 1 – Manipulação e Validação de Dados
* **Validação de Objetos:** Filttragem de um array de pedidos garantindo que o cliente não seja vazio e que o valor numérico seja maior que zero.
* **Filtro por Status:** Isolamento de pedidos válidos com o status `"pago"`.
* **Acumulação com `reduce`:** Cálculo do faturamento total acumulado do array filtrado.
* **Formatação Monetária:** Geração de textos monetários amigáveis no formato `"Bia - R$ 120.00"` utilizando o método `.toFixed(2)`.

### Parte 2 – Mini Projeto: Buscador de CEP
* **Interface e Validação:** Entrada de dados tratada com `.trim()` e expressões regulares (Regex) para garantir a formatação exata de 8 dígitos numéricos.
* **Consumo Assíncrono:** Integração com a API ViaCEP (`https://viacep.com.br{cep}/json/`) utilizando `fetch` combinado com a sintaxe moderna de `async/await`.
* **Tratamento dos Quatro Estados:**
  * **Carregando:** Exibição do aviso *"Buscando..."* e desabilitação do botão enquanto a requisição é processada.
  * **Erro:** Captura de falhas de conexão à rede ou erros HTTP por meio de verificações lógicas baseadas em `!response.ok`.
  * **Vazio/Não Encontrado:** Tratamento de retornos específicos de chaves de erro da API para exibir *"CEP não encontrado"*.
  * **Sucesso:** Limpeza de estados anteriores através do método `replaceChildren()`, renderização dinâmica de linhas (`<tr>` e `<td>`) com `createElement` e alimentação segura de dados usando `textContent` (prevenindo vulnerabilidades de XSS).
* **Bônus:** Armazenamento interno de um histórico de CEPs já pesquisados, listando-os em tela como um array de objetos.

### Parte 3 – Tarefa de Casa: Desafio Mini Pokédex
* **Campo de Busca:** Input textual validado para entradas não vazias e automaticamente convertido para letras minúsculas (`.toLowerCase()`).
* **Consumo de API Externa:** Conexão com a API PokéAPI (`https://pokeapi.co{nome}`) utilizando `fetch` estruturado com `async/await`.
* **Renderização Dinâmica:** Exibição da imagem do Pokémon (`sprites.front_default`), nome e tipos.
* **Tratamento de Estado 404:** Interpolação e verificação de erros HTTP 404 explicitamente tratados para lançar e exibir o aviso de *"Pokémon não encontrado"*.

---

## 🧠 Parte 4 – Reflexão Teórica (Para Pensar)

### Por que `Promise.all` pode ser mais rápido que vários `await` seguidos?
Quando utilizamos múltiplos comandos `await` em sequência, o interpretador do JavaScript executa as requisições de forma **síncrona/sequencial**. Isso significa que a segunda requisição só será iniciada após a primeira terminar completamente, acumulando o tempo de resposta de cada uma individualmente.

O `Promise.all`, por outro lado, **dispara todas as requisições em paralelo**. Ele envia todas as promessas para a Web API simultaneamente e aguarda até que a última delas termine de ser resolvida. Dessa forma, aproveitamos ao máximo o canal de rede e reduzimos o tempo de espera total da aplicação para o tempo da requisição mais lenta, otimizando drasticamente a performance.

---

## 🚀 Como Executar o Projeto

1. Baixe os arquivos `index.html` e `app.js` na mesma pasta de desenvolvimento.
2. Abra o arquivo `index.html` no seu navegador web de preferência.
3. Teste o comportamento assíncrono inserindo CEPs ou nomes de Pokémons nos campos correspondentes e observe as mudanças de estado visuais e os tratamentos contra erros no Console de Desenvolvedor (**F12**).

---

## ✍️ Autoria
Atividade acadêmica desenvolvida para a disciplina de **Desenvolvimento Web** (Semana 05).  
**Universidade CEUMA.**
