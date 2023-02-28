<p align="center"> <img src="https://imgur.com/mIBmcEL.png" alt="Javascript: validando formulários"> </p>

<hr>

<p align="center"> <img src="https://github.com/MonicaHillman/aluraplay-requisicoes/blob/main/img/logo.png" alt="Logo da Alura"> </p>
<p align="center">Formulário de criação de contas para o banco virtual ViniBank.</p>

## Tecnologias utilizadas durante o curso
* JavaScript

## Tecnologias utilizadas no projeto
* HTML
* CSS

<h1>Módulo 01: Validando com HTML</h1>

<h2>03. Tipos de input</h2>

<p>Estamos trabalhando com a criação de contas no Monibank. Para conseguir mexer no projeto, precisamos primeiro abri-lo no Visual Studio Code e preparar nosso ambiente. Para isso, abriremos a IDE no computador. Na aba do menu de "Introdução", vamos até a terceira opção, "Abrir a pasta..." . Também é possível abrir o arquivo na opção "Arquivo", no menu superior do Visual Studio Code.</p>

<p>Clicaremos em "Abrir a Pasta" e o sistema abrirá o explorador de arquivos do computador. Acessaremos o caminho "Documentos > dev > monibank".</p>

<p>Dica: criaremos uma pasta para cada projeto, assim evitamos confusões e não corremos o risco de inserir o arquivo de um projeto dentro de outro.</p>

<p>Clicaremos na opção "Selecionar Pasta" que abrirá o projeto no Visual Studio Code. Vamos olhar primeiro o que precisamos fazer no formulário, acessando-o através do navegador. Essa primeira parte do formulário possui vários campos: "nome", "e-mail", "RG", "CPF", "data de nascimento", um texto sobre aceitar as políticas de privacidade do banco e um botão de avançar.</p>

<p>Podemos ver que não são padrões iguais: o campo de e-mail possui uma estrutura com nome, seguido de um arroba (@) e uma URL. Já o campo de nome possui vários caracteres que formam o nome de alguém — por exemplo, o meu, que é Monica. Então, como podemos através do HTML criar um padrão que condicione a inserção de dados a seguir regras específicas?</p>

<p>Voltando ao Vs Code, acessaremos o arquivo abrir-conta-form que está dentro da pasta "pages" para verificarmos o código desse formulário. Na linha 55, acessamos o elemento pai de todos, o form class= "principal__formulario". Nele temos as seções abaixo:</p>

<p>
    - "nome", "rg" e "cpf" nas quais adicionaremos o tipo texto através do type = "text";
    - email, na qual adicionaremos um type = "email";
    - "aniversario", na qual adicionaremos um type = "date" e
    - o campo "termos" no qual adicionaremos um type = "checkbox";
    - um input que possui o texto "Avançar", no qual adicionaremos um type = "submit".
</p>

```
            <form class="principal__formulario" data-formulario>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="nome">Nome</label>
                    <input name="nome" id="nome" class="campo__escrita" type="text" minlength="3" required />
                    <span class="mensagem-erro"></span>
                </fieldset>

                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="email">E-mail</label>
                    <input name="email" id="email" class="campo__escrita" type="email" minlength="4" required />
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="rg">RG</label>
                    <input name="rg" id="rg" class="campo__escrita campo__escrita--menor" type="text" required />
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="cpf">CPF (apenas números)</label>
                    <input name="cpf" id="cpf" class="campo__escrita campo__escrita--menor" required type="text"
                    minlength="11" maxlength="14" />
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="aniversario">Data de nascimento</label>
                    <input name="aniversario" id="aniversario" class="campo__escrita campo__escrita--menor" type="date"
                        required />
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__termos">
                    <input name="termos" class="termos__input" type="checkbox">
                    <p class="termos__texto">Li e estou ciente quanto às condições de tratamento dos meus dados conforme descrito na Política de Privacidade do banco.</p>
                    <span class="mensagem-erro"></span>
                </fieldset>

                <div>
                    <input value="Avançar" class="formulario__botao" id="enviar" data-botao-enviar type="submit">
                    <span class="mensagem-erro"></span>
                </div>
            </form>COPIAR CÓDIGO
```

<p>Salvaremos o código e veremos o que mudou visualmente na nossa tela. Agora temos o campo de "data de nascimento" com um padrão de data em seu interior: "dia/mês/ano". No último campo do formulário onde inserimos um checkbox agora aparece um quadrado selecionável.</p>

<p>Vamos entender o que são cada um desses tipos. Nos types de "nome", "RG" e "CPF" colocamos o tipo texto porque ele vai aceitar tanto os caracteres de letras quanto os numéricos. No type do e-mail inserimos email que se constitui do padrão de e-mails: nome + @ + URL do e-mail", como por exemplo gmail e outlook.</p>

<p>No campo "Data de nascimento" temos um tipo date, que constitui o formato de data: "dd/mm/aaaa", os quais indicam dia, mês e ano, respectivamente. Se clicarmos em cima do seu input, surge um calendário com dias, meses e anos para facilitar o preenchimento, deixando o processo intuitivo para a pessoa usuária.</p>

<p>O input de caixa de seleção na seção temos se transformou num quadrado que quando selecionado será preenchido com um símbolo de check. Geralmente utilizamos essa ferramenta pala inserir várias opções para aceite. Nesse caso é só uma, entretanto utilizamos essa ferramenta para deixar a concordância com a política de privacidade do banco mais intuitiva. O type = "submit" que inserimos no botão "Avançar" serve pra enviar todos os dados do formulário pra um lugar determinado no JavaScript que ainda não configuramos.</p>

<p>Podemos perceber que nos campos de RG e CPF inserimos um tipo de texto, mas quando procuramos essas partes em um documento, são na verdade números.</p>

<p>Então por que configuramos como tipo texto? Temos que ter em mente que quando queremos inserir um tipo de número, estamos falando de quantidade. CPF RG não são quantidades, e sim um conjunto de caracteres que que individualizam cada pessoa do Brasil. Outro detalhe: o RG não possui padrão. Dependendo do Estado, ele pode ter números, letras e traços. O CPF, por enquanto, possui apenas números, mas essa característica pode mudar no futuro. Ele também possui um formato específico: três sequências de três números separadas por um ponto e uma sequência de dois números separada por um traço: "000.000.000-00".</p>

<p>Declaramos os tipos de cada formulário para garantir o padrão atual. Se colocarmos algum texto no campo de e-mail como teste e clicarmos em "Avançar", aparecerá uma caixa com uma mensagem de erro informando que precisamos inserir o @ e a URL depois dele, ou seja, a aplicação está cobrando que o padrão de inserção seja igual ao padrão do HTML.</p>

<p>Já fizemos esse tipo de validação, mas não atingimos o máximo que podemos fazer em HTML. Em seguida, veremos outra coisa que vai ajudar nessa questão de validações somente com HTML. Eu te vejo no próximo vídeo!</p>