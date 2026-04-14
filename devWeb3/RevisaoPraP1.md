Fala, mestre! Tudo certo? Vamos resolver essa lista de revisão da FATEC agora mesmo. Preparei os códigos comentados e as explicações detalhadas para cada questão, focando no funcionamento do Node.js.

Aqui estão as resoluções da atividade do **Prof. [cite_start]Vinicius Heltai [cite: 24]**:

---

## Questão 01: Sistema de Configuração (Módulo `fs` e JSON)

Nesta questão, o objetivo é manipular arquivos JSON e entender a leitura assíncrona.

[cite_start]**Passo 1: Preparação [cite: 3, 4]**
* No terminal: `npm init -y`
* Arquivo `config.json`:
    ```json
    {
      "campus": "Diadema",
      "curso": "Desenvolvimento de Software Multiplataforma",
      "semestre": "3º"
    }
    ```

[cite_start]**Passo 2: Script `index.js` [cite: 5]**
```javascript
const fs = require('fs');

// Lendo o arquivo de forma assíncrona
fs.readFile('config.json', 'utf8', (err, data) => {
    if (err) {
        console.error("Erro ao ler o arquivo:", err);
        return;
    }
    
    // Convertendo o texto do arquivo para um objeto JavaScript
    const config = JSON.parse(data);
    
    // Exibindo a mensagem formatada
    console.log(`Configuração carregada para o curso ${config.curso} no campus ${config.campus}`);
});
```

> **Explicação Detalhada:**
> [cite_start]* **`fs.readFile`**: É uma função assíncrona que não trava a execução do programa enquanto o disco lê o arquivo[cite: 5].
> * **`JSON.parse(data)`**: O arquivo é lido como uma "string" bruta. Para acessar as propriedades como `config.curso`, precisamos transformá-la em um objeto.

---

## Questão 02: Sistema de Logs (Append e Verificação de Arquivo)

[cite_start]Aqui trabalhamos com a persistência de dados e manipulação de datas[cite: 6].

[cite_start]**Configuração `package.json`[cite: 7]:**
```json
"scripts": {
  "start": "node index.js"
}
```

[cite_start]**Script de Log[cite: 8, 9, 10]:**
```javascript
const fs = require('fs');

const logPath = 'log.txt';
const agora = new Date().toLocaleString();
const novaEntrada = `Novo acesso registrado em: ${agora}\n`;

// fs.appendFile cria o arquivo se não existir e adiciona ao final se existir
fs.appendFile(logPath, novaEntrada, (err) => {
    if (err) throw err;
    console.log('Log atualizado com sucesso!');
});
```

> **Explicação Detalhada:**
> [cite_start]* **`fs.appendFile`**: Esta função é extremamente útil pois ela resolve dois problemas de uma vez: se o arquivo `log.txt` não existir, o Node o cria; se já existir, ele apenas adiciona o conteúdo ao final (append), sem apagar o que já estava lá[cite: 9, 10].
> [cite_start]* **`new Date()`**: Captura a estampa de tempo (timestamp) atual do servidor[cite: 9].

---

## Questão 03: API de Consulta Acadêmica (Servidor HTTP e JSON)

[cite_start]O foco aqui é o cabeçalho de resposta (`Content-Type`) e rotas básicas[cite: 11].

[cite_start]**Script do Servidor[cite: 12, 13, 14]:**
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    if (req.url === '/') {
        res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
        res.end('<h1>Portal de APIs Acadêmicas</h1>');
    } 
    else if (req.url === '/instituicao') {
        const dados = {
            nome: "Faculdade Tecnológica de São Paulo",
            cidade: "São Paulo",
            status: "online"
        };
        res.writeHead(200, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify(dados));
    }
});

server.listen(3000, () => console.log('Servidor rodando na porta 3000'));
```

> **Explicação Detalhada:**
> * **`res.writeHead`**: Informa ao navegador o que ele está recebendo. [cite_start]Se for `text/html`, ele renderiza como página; se for `application/json`, ele entende como dados[cite: 14].
> [cite_start]* **`JSON.stringify`**: Transforma o objeto JavaScript em uma string JSON para que possa ser enviado via protocolo HTTP[cite: 13].

---

## Questão 04: Roteador Institucional (Tratamento de URL e Status 404)

[cite_start]Nesta questão, exercitamos a lógica de rotas e o envio de códigos de erro[cite: 15, 18].

[cite_start]**Script do Roteador[cite: 16, 17, 18]:**
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    const url = req.url;

    res.setHeader('Content-Type', 'text/plain; charset=utf-8');

    if (url === '/fatec') {
        res.statusCode = 200;
        res.end("Bem-vindo à Faculdade de Tecnologia");
    } 
    else if (url === '/fecap') { // Nota: Conforme solicitado na questão 4
        res.statusCode = 200;
        res.end("Bem-vindo a FATEC Diadema");
    } 
    else {
        res.statusCode = 404;
        res.end("Recurso não encontrado no servidor");
    }
});

server.listen(3000);
```

> **Explicação Detalhada:**
> [cite_start]* **`res.statusCode`**: O status `200` indica sucesso, enquanto o `404` é o código padrão mundial para "Não Encontrado"[cite: 17, 18].
> [cite_start]* **Lógica de Roteamento**: O servidor analisa a `req.url` para decidir qual bloco de código executar[cite: 18].

---

## Questão 05: Automação de Dados (Leitura de CSV e Exportação)

[cite_start]Simulamos um processo de ETL (Extração, Transformação e Carregamento) simples[cite: 19].

[cite_start]**Configuração `package.json`[cite: 23]:**
```json
"scripts": {
  "export": "node export.js"
}
```

[cite_start]**Script `export.js`[cite: 20, 21, 22]:**
```javascript
const fs = require('fs');

const input = 'estudantes.csv';
const output = 'export_relatorio.txt';
const dataAtual = new Date().toLocaleDateString();

fs.readFile(input, 'utf8', (err, conteudo) => {
    if (err) {
        console.log("Crie o arquivo estudantes.csv primeiro!");
        return;
    }

    const cabecalho = `Relatório Gerado para FATEC [${dataAtual}]\n`;
    const resultadoFinal = cabecalho + conteudo;

    fs.writeFile(output, resultadoFinal, (err) => {
        if (err) throw err;
        console.log(`Relatório exportado para ${output}`);
    });
});
```

> **Explicação Detalhada:**
> [cite_start]* **Workflow**: O script primeiro lê todo o conteúdo do CSV para a memória e depois escreve um novo arquivo concatenando o cabeçalho solicitado[cite: 21, 22].
> * **`npm run export`**: É um comando customizado. [cite_start]Diferente do `start`, comandos criados por você exigem a palavra `run`[cite: 23].

---

## Lista de Artigos para Estudo

Para dominar esses tópicos de Desenvolvimento Web III, recomendo a leitura destes temas:

1.  **Node.js File System (fs) - Documentação Oficial:** Para entender todas as variações de leitura e escrita (Sync vs Async).
2.  **Anatomy of an HTTP Transaction:** Artigo oficial do Node.js sobre como lidar com `req` (requisição) e `res` (resposta).
3.  **Entendendo Códigos de Status HTTP (MDN Web Docs):** Essencial para saber quando usar 200, 201, 404 ou 500.
4.  **Trabalhando com JSON no JavaScript (MDN):** Para dominar as funções `JSON.parse()` e `JSON.stringify()`.

Boa sorte na P1! Se precisar de mais algum ajuste nos códigos, é só avisar.