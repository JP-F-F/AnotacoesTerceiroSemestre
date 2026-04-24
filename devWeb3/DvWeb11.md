# Dv. Web 3 - aula 11 - Node.js/JSON web service e primeiros passos

## Promises/Promessas

Promises são objetos que representam a eventual conclusão(ou falha) de uma operação assíncrona e fornecem uma maneira de lidar com resultados assíncronos e sincronos de forma prática.

A gente usa as promises basicamente para mandar nosso programa fazer outra coisa enquanto ele espera que uma tarefa longa seja concluida.

As **promises** tem 3 estados:
* Pending(pendente) - Quando ela é criada;
* FulFilled(realizada) - Quando a operação assíncrona é concluída com sucesso, passando para o estado cumprido e retorna um valor ou resultado.
* Rejected(rejeitada) - Se a operação falha, a promise passa para o estado rejeitado e retorna um erro.

**Metodo thn/catch com promises**

Com promises, podemos usar o método `then()` para tratar resultados bem sucedidos e o `catch()` para tratar os erros.

EX:
````javascript

let minhaPromise = new Promise(function(resolve, reject){
    //faça algo, se der certo chama o resolve, se não chame o reject
});

minhaPromise.then(function(resultado){
    //trata o resultado bem-sucedido
}).catch(function(erro){
    //trata o erro
})
````

Como os métodos **Promise.prototype.then** e **Promise.prototype.catch** retornam ***PROMISES***, eles podem ser encadeados.

## Callback

_Callbacks_ são funções que são passadas como **argumento para outras funções** e são chamadas quando algum **evento/operação assíncrona é resolvidos**. Basicamente estas são funções que são executadas após outra função concluir sua execução.

EX:

````javascript

function calcula(num1, num2, callback){
    const resultado = num1 + num2;
    callback(resultado);
}

function imprimeResultado(resultado){
    console.log(`O resultado da operação é: ${resultado}`);
}

// Chamando a função calcula passando os argumentos e a função callback
calcula(1, 1, imprimeResultado());
````

## Async e Await

A programação async e await é uma técnica utilizada em linguagens de programação modernas, para **lidar com operações assíncronas de for síncrona**.

O **async/await** facilitaram bastante a escrever códigos, pois podemos usar agora a palavra-chave **async** antes de uma função assíncrona e **await** antes das chamadas dessas operações. Para capturar erros dessas operações podemos simplesmente usar o _try/catch_.

EX:

````javascript

async function fetchUserData(){
    try{
        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
        const data = await response.json();
        console.log(data);
    }catch(error){
        console.error(error);
    }
}

fetchUserData();

````

## Primeiros passos com Node.js

**Desenvolvendo a estrutra do projeto**

Todo projeto em node.js tem presente algumas estruturas, uma delas é o **package.json** que é um arquivo de configuração. usamos o comando `npm init -y` para cria-lo, o "-y" é opcional ele determina tudo como "yes", assim criando um arquivo padrão.
