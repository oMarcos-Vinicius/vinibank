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
            </form>
```

<p>Salvaremos o código e veremos o que mudou visualmente na nossa tela. Agora temos o campo de "data de nascimento" com um padrão de data em seu interior: "dia/mês/ano". No último campo do formulário onde inserimos um checkbox agora aparece um quadrado selecionável.</p>

<p>Vamos entender o que são cada um desses tipos. Nos types de "nome", "RG" e "CPF" colocamos o tipo texto porque ele vai aceitar tanto os caracteres de letras quanto os numéricos. No type do e-mail inserimos email que se constitui do padrão de e-mails: nome + @ + URL do e-mail", como por exemplo gmail e outlook.</p>

<p>No campo "Data de nascimento" temos um tipo date, que constitui o formato de data: "dd/mm/aaaa", os quais indicam dia, mês e ano, respectivamente. Se clicarmos em cima do seu input, surge um calendário com dias, meses e anos para facilitar o preenchimento, deixando o processo intuitivo para a pessoa usuária.</p>

<p>O input de caixa de seleção na seção temos se transformou num quadrado que quando selecionado será preenchido com um símbolo de check. Geralmente utilizamos essa ferramenta pala inserir várias opções para aceite. Nesse caso é só uma, entretanto utilizamos essa ferramenta para deixar a concordância com a política de privacidade do banco mais intuitiva. O type = "submit" que inserimos no botão "Avançar" serve pra enviar todos os dados do formulário pra um lugar determinado no JavaScript que ainda não configuramos.</p>

<p>Podemos perceber que nos campos de RG e CPF inserimos um tipo de texto, mas quando procuramos essas partes em um documento, são na verdade números.</p>

<p>Então por que configuramos como tipo texto? Temos que ter em mente que quando queremos inserir um tipo de número, estamos falando de quantidade. CPF RG não são quantidades, e sim um conjunto de caracteres que que individualizam cada pessoa do Brasil. Outro detalhe: o RG não possui padrão. Dependendo do Estado, ele pode ter números, letras e traços. O CPF, por enquanto, possui apenas números, mas essa característica pode mudar no futuro. Ele também possui um formato específico: três sequências de três números separadas por um ponto e uma sequência de dois números separada por um traço: "000.000.000-00".</p>

<p>Declaramos os tipos de cada formulário para garantir o padrão atual. Se colocarmos algum texto no campo de e-mail como teste e clicarmos em "Avançar", aparecerá uma caixa com uma mensagem de erro informando que precisamos inserir o @ e a URL depois dele, ou seja, a aplicação está cobrando que o padrão de inserção seja igual ao padrão do HTML.</p>

<p>Já fizemos esse tipo de validação, mas não atingimos o máximo que podemos fazer em HTML. Em seguida, veremos outra coisa que vai ajudar nessa questão de validações somente com HTML. Eu te vejo no próximo vídeo!</p>

<h2>05. Min-lenght e Max-length</h2>

<p>Já inserimos os tipos em cada elemento HTML para que o conteúdo possa seguir um padrão de acordo com o objetivo de cada campo. Nos aventuraremos em outro problema: como regulamos a quantidade de caracteres em cada campo para evitar que a pessoa usuária insira dados incorretos?</p>

<p>Acessaremos o arquivo abrir-conta-form.html em nossa IDE, e na seção input name="nome" adicionaremos um minLength de 3. Este atributo determina a quantidade mínima de caracteres que deve ser inserida e impede que um campo seja mantido vazio. Já na seção input name="email" adicionaremos um minLength de 4. Por último, adicionaremos um minLength de tamanho 11 na seção input name="cpf". O rg não possuirá um valor mínimo de caracteres, pois conforme vimos anteriormente, cada estado possui um padrão diferente.</p>

<p>Observação: não existe um padrão para o valor do minLength.</p>

<p>No campo de CPF, adicionaremos um maxLength="14" para definir também a quantidade máxima, visto que esse documento pode possuir ou não caracteres especiais.</p>

```
            <form class="principal__formulario" data-formulario>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="nome">Nome</label>
                    <input name="nome" id="nome" class="campo__escrita" type="text" minlength="3"/>
                    <span class="mensagem-erro"></span>
                </fieldset>

                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="email">E-mail</label>
                    <input name="email" id="email" class="campo__escrita" type="email" minlength="4"/>
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="rg">RG</label>
                    <input name="rg" id="rg" class="campo__escrita campo__escrita--menor" type="text"/>
                    <span class="mensagem-erro"></span>
                </fieldset>
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="cpf">CPF (apenas números)</label>
                    <input name="cpf" id="cpf" class="campo__escrita campo__escrita--menor" required type="text"
                        minlength="11" maxLength="14"/>
                    <span class="mensagem-erro"></span>
                </fieldset>
                // Trecho de código omitido
```

<p>Salvaremos o nosso código e acessaremos a aplicação novamente pelo navegador. No campo "Nome", se digitarmos qualquer texto com menos de três caracteres, uma mensagem uma será exibida abaixo do campo selecionado solicitando que aumentemos o texto para três caracteres ou mais. Já no campo "E-mail", se digitarmos um texto, um "@" e mais nada, será exibida uma mensagem solicitando que adicionemos um texto após esse símbolo. Por sua vez, no campo "CPF", se adicionarmos menos de onze caracteres, será exibida uma mensagem solicitando que preenchamos o total necessário — e se tentarmos preencher mais do que quatorze caracteres, o sistema para de inclui-los a partir do décimo quinto.</p>

<p>Conseguimos realizar ainda mais tarefas com o HTML. No próximo vídeo veremos outro atributo que nos ajudará a validar os elementos do formulário.</p>

<h2>06. Required</h2>

<p>Já definimos os tipos para cada campo de digitação e também os números mínimo e máximo de caracteres que devem ser inseridos em cada um deles. Existe mais um elemento a ser incluído em nosso HTML: o atributo required ("obrigatório", em português), que torna obrigatório o preenchimento de um campo.</p>

<p>Se repararmos na seção input name="cpf", aproximadamente na linha 80, já existe um required configurado para o campo de CPF. Vamos incluí-lo nos campos de "Nome", "E-mail", "RG", "Data de nascimento" e também no checkbox de aceite dos termos do banco.</p>

<p>Atributo required no campo "CPF":</p>

```
                        <input name="cpf" id="cpf" class="campo__escrita campo__escrita--menor" required type="text"
```

<p>Atributo required nos campos "Nome", "E-mail", "RG" e "Data de nascimento" e no checkbox de aceite dos termos:</p>

```
                        <input name="nome" id="nome" class="campo__escrita" type="text" minlength="3" required />
                        // Trecho de código omitido
                        <input name="email" id="email" class="campo__escrita" type="email" minlength="4" required />
                        // Trecho de código omitido
                        <input name="rg" id="rg" class="campo__escrita campo__escrita--menor" type="text" required />
                        // Trecho de código omitido
                        <input name="aniversario" id="aniversario" class="campo__escrita campo__escrita--menor" type="date" required />
                        // Trecho de código omitido
                         <input name="termos" class="termos__input" type="checkbox" required>
```

<p>Agora não será mais possível enviar o formulário enquanto tivermos campos em branco. Isso evita que apareçam campos com valores vazios em nosso código.</p>

<p>Realizamos vários tipos de validação com o HTML. A seguir iremos mais além nessas validações e partiremos para o Javascript. Nos vemos lá!</p>

<h1>Módulo 02: Validando com JS</h1>

<h2>02. Pattern e Regex</h2>

<p>Aprendemos anteriormente que o campo de CPF é constituído de três grupos de três dígitos e um grupo de dois dígitos, onde cada grupo é separado por caracteres especiais como ponto e hífen. Como configuramos o sistema para que siga esse padrão?</p>

<p>Na seção input name="cpf", após o atributo maxLength, adicionaremos um pattern que possuirá o comando "\d{3}\.?" repetido três vezes, sendo que na última repetição o ponto (.) deverá ser substituído por traço (-). Por fim, ainda no interior deste comando, adicionaremos "\d{2}".</p>

```
 <input name="cpf" id="cpf" class="campo__escrita campo__escrita--menor" required type="text" minlength="11" maxlength="14" pattern="\d{3}\.?\d{3}\.?\d{3}-?\d{2}"/>
```

<p>Este tipo de código é chamado de Expressão Regular, ou Regex. O único requisito para a sua utilização é introduzi-lo dentro de um pattern. Este por sua vez criará um formato específico que deve ser seguido pelo conteúdo inserido — em nosso caso o CPF. Vamos analisar a expressão regular que utilizamos acima:</p>

<p>
    - o trecho \d{3}\ agrupa um número de 0 a 9 por três vezes;
    - o trecho .? indica que o grupo de dígitos poderá ser seguido por um ponto, onde o ? indica que esse critério é opcional.
    - o trecho -? indica que o grupo de dígitos poderá ser seguido por um traço, critério que também é opcional.
    - o trecho final \d{2} agrupa um número de 0 a 9 por duas vezes.
</p>

<p>Esta combinação de comandos cria o formato para o CPF que informamos anteriormente, garantindo que sejam aceitos inputs com e sem pontuação.</p>

<p>Caso queira saber mais sobre Expressões Regulares, acesse a seção "Para saber mais" sobre expressões regulares deste curso.</p>

<p>A seguir começaremos a preparar o nosso projeto para receber validações customizadas diretamente pelo Javascript. Nos vemos lá!</p>

<h2>03. AddEventListener</h2>

<p>Até o momento criamos validações somente em HTML, o que limita um pouco nossas opções. Temos dois campos dedicados exclusivamente a documentos brasileiros cujo padrão não existe em HTML, e por isso precisamos criar uma lógica por trás destes campos. Para isso criaremos um arquivo Javascript. Acessaremos o explorador do Visual Studio Code, selecionaremos a pasta "monibank" e clicaremos no ícone de "New Folder" (ou "Nova Pasta") na barra superior do explorador. Essa nova pasta se chamará "js". Em seu interior criaremos o arquivo script.js clicando no ícone de "New File" ("Novo Arquivo") também localizado na barra superior do explorador.</p>

<p>Acessaremos novamente o arquivo abrir-conta-form.html. Após a seçção <\footer> e antes de <\body> importaremos o arquivo JS, inserindo um type="module". Desta forma incluiremos nesta página toda a lógica que será implementada no arquivo Javascript.</p>

```
        //Trecho de código omitido
    </footer>
    <script src="../js/script.js" type="module"></script>
</body>
```

<p>Separaremos cada motivação em um arquivo diferente, que serão unidos em um único script. Esta técnica se chama modularização. Para que ela funcione corretamente, precisamos especificar o tipo module.</p>

<p>Após realizarmos essa associação, retornaremos ao arquivo script.js e criaremos a variável camposDoFormulario do tipo constante (const) que receberá todos os elementos do HTML que possuem o atributo required — ou seja, todos os elementos de preenchimento obrigatório.</p>

```
const camposDoFormulario = document.querySelectorAll("[required]");
```

<p>Vamos verificar a lista de elementos captados através de um console.log.</p>

```
console.log(camposDoFormulario);
```

<p>Em seguida abriremos no navegador a página de formulário do Monibank e também a aba "Console" no interior da aba "Ferramentas do Desenvolvedor", que pode ser acessada através do atalho "Ctrl + Shift + I". Veremos em "Console" uma NodeList com os seis elementos de input da tela já selecionados. Precisamos adicionar um comando que "ouça" o evento de digitação em cada campo para em seguida realizar as validações.</p>

<p>Retornando ao arquivo script.js, deletaremos o console.log e adicionaremos a variável camposDoFormulario junto ao comando forEach, que possuirá uma função seta ("arrow function", em inglês) (campo) => {}. No interior dos colchetes adicionaremos um campo.addEventListener() que possuirá um "blur" e outra função de seta que chamará verificaCampo, que por sua vez receberá o valor de campo. Configuraremos 'a função verificaCampo posteriormente.</p>

```
    camposDoFormulario.forEach((campo) => {
        campo.addEventListener("blur", () => verificaCampo(campo));
    })
<
```

<p>Vamos entender o trecho de código que implementamos? Cada campo do formulário será recuperado pela função forEach e chamado de campo, que por sua vez possuirá um event listener aguardando o evento blur acontecer. O blur ("desfoque", em português) se caracteriza por um clique fora do input, ou seja, assim que o campo que estava sendo preenchido estiver fora de foco, o event listener disparará a função verificaCampo.</p>

<p>Finalmente criaremos a base da função verificaCampo().</p>

```
    camposDoFormulario.forEach((campo) => {
        campo.addEventListener("blur", () => verificaCampo(campo));
    })
    
    function verificaCampo(campo){
    
    }
```

<p>A seguir, colocaremos a mão na massa e construiremos a verificação no interior desta função. Nos vemos lá!</p>

<h2>05. Verificar CPF</h2>

<p>Vamos relembrar? Quando importamos o arquivo script.js dentro do HTML definimos o tipo module pois as validações seriam separadas em arquivos diferentes e se encontrariam no script. Vamos colocar essa funcionalidade em prática iniciando pelas validações de CPF.</p>

<p>Acessaremos o explorador, clicaremos na pasta "js" e em seguida no ícone de "Novo Arquivo". Daremos a este novo arquivo o nome valida-cpf.js. No interior dele adicionaremos um export default function com a função ehumCPF() que receberá um campo. Dentro dessa função criaremos uma variável const chamada cpf que receberá o comando campo.value.replace(/\.|-g,""). Adicionaremos também um console.log para imprimir o resultado.</p>

```
export default function ehUmCPF(campo) {
    const cpf = campo.value.replace(/\.|-/g, "");
    console.log(cpf);
}
```

<p>Vamos entender este trecho de código? A função ehUmCPF foi configurada para ser exportada como padrão, ou seja, quando chamarmos o arquivo valida-cpf esta função será retornada. Criamos também uma função tradicional que receberá o valor de campo com o método replace, que por sua vez recebe dois parâmetros: o primeiro indica o conteúdo que queremos substituir (no caso, os caracteres especiais . e -), enquanto o segundo indica o conteúdo que será utilizado para substituí-lo (no caso, um campo vazio). Através desta função, efetuamos a remoção dos caracteres especiais nos casos de inputs com essa característica, normalizando esses valores e tornando mais fácil a comparação e validação entre os tipos de CPF inseridos.</p>

<p>Salvaremos o código e acessaremos o arquivo script.js. Na linha 1, acima da variável const camposDoFormulario, adicionaremos o ìmport da função ehUmCPF para habilitarmos o seu uso.</p>

```
import ehUmCPF from "./valida-cpf.js";
```

<p>Adicionaremos no interior da function verificaCampo um if que retorna a função ehUmCPF nos casos em que o nome do campo for "cpf" e seu valor for maior ou igual a 11.</p>

<p>Observação: Nos casos que fogem a esta regra, um outro erro deverá ser retornado. Não o abordaremos neste momento.</p>

```
import ehUmCPF from "./valida-cpf.js";
const camposDoFormulario = document.querySelectorAll('[required]')

camposDoFormulario.forEach((campo) => {
    campo.addEventListener("blur", () => verificaCampo(campo));
})

function verificaCampo(campo) {
    if (campo.name == "cpf" && campo.value.length >= 11) {
        ehUmCPF(campo);
    }
}
```

<p>Se retornarmos ao navegador e digitarmos um valor numérico qualquer no campo de CPF, veremos que ele será retornado na aba "Console". Se digitarmos um cpf com caracteres especiais, ele será retornado no Console sem estes caracteres.</p>

<p>Dica: para encontrar um CPF válido com caracteres especiais, utilize o site Gerador de CPFs disponível neste link.</p>

<p>Já chamamos um arquivo externo e transformamos os valores de CPF em números simples. Em seguida configuraremos as validações em si.</p>

<p>A primeira etapa é configurar a validação de números repetidos, já que não existem CPFs com todos os números iguais, como por exemplo "111.111.111-11". Para isso acessaremos o arquivo valida-cpf.js e criaremos a função validaNumerosRepetidos() que receberá o valor de cpf. Em seu interior criaremos a lista const numerosRepetidos que receberá todas as combinações de 11 números repetidos, de 0 até 9.</p>

```
function validaNumerosRepetidos(cpf) {
    const numerosRepetidos = [
    '00000000000',
    '11111111111',
    '22222222222',
    '33333333333',
    '44444444444',
    '55555555555',
    '66666666666',
    '77777777777',
    '88888888888',
    '99999999999'
    ]
```

<p>Dessa forma conseguimos verificar se o número que inserimos no campo de CPF está nessa lista de números repetidos. Para isso criaremos um return com o método numerosRepetidos.includes(cpf). Caso o valor do CPF inserido seja encontrado na lista de repetições, o método retornará true, caso contrário retornará false.</p>

```
function validaNumerosRepetidos(cpf) {
    const numerosRepetidos = [
    '00000000000',
    '11111111111',
    '22222222222',
    '33333333333',
    '44444444444',
    '55555555555',
    '66666666666',
    '77777777777',
    '88888888888',
    '99999999999'
    ]

    return numerosRepetidos.includes(cpf)
}
```

<p>Chamaremos a função validaNumerosRepetidos no interior da função ehUmCPF, substituindo o console.log que deletamos anteriormente. Adicionaremos logo abaixo um novo console.log que retornará a própria chamada da função.</p>

```
export default function ehUmCPF(campo) {
    const cpf = campo.value.replace(/\.|-/g, "");
    validaNumerosRepetidos(cpf);

    console.log(validaNumerosRepetidos(cpf));
}
```

<p>Salvaremos o nosso código e retornaremos ao navegador para testá-lo. Recolheremos outro CPF do site Gerador de CPFs e colaremos em nosso campo de CPF. Assim que clicarmos fora do campo, o Console retornará false, pois o valor que inserimos não possui números repetidos. Se digitarmos um número repetido, como por exemplo, "22222222222", e clicarmos fora do campo, o Console retornará true.</p>

<p>Já conseguimos descobrir se existem números repetidos no campo de CPF. Contudo, esta validação é básica comparada a outras possibilidades de validação de um CPF. A seguir, realizaremos outras validações mais profundas. Nos vemos lá!</p>

<h1>Módulo 03: Desenvolvendo Validações</h1>

<h2>02. CPF: primeiro dígito</h2>

<p>Anteriormente tratamos a ocorrência de vários números repetidos dentro do campo de CPF. Agora realizaremos um procedimento mais complexo: a validação do primeiro dígito verificador (o primeiro dígito imediatamente após o traço). Para isso acessaremos o final do arquivo valida-cpf.js, abaixo da seção return numerosRepetidos.includes(cpf) e ali adicionaremos uma nova função: validaPrimeiroDigito() informando em seu interior o cpf. Dentro das chaves desta função criaremos duas variáveis:</p>

<p>
    - let soma, que receberá o valor 0;
    - let multiplicador que receberá o valor 10.
</p>

<p>Ainda no interior da função, criaremos um laço de repetição for que possuirá a variável let tamanho = 0, a qual determinaremos que deve se repetir nove vezes (para os 9 primeiros dígitos do CPF) através do comando tamanho < 9; tamanho++. Em seguida adicionaremos no interior das chaves deste for a variável soma que declaramos anteriormente e que agora deverá recolher os valores do CPF de acordo com cada posição do for. Em seguida vamos multiplicá-lo pelo valor de multiplicador. Na linha de baixo adi</>cionaremos o comando multiplicador-- que completará o loop duplo no qual o CPF aumenta a posição do tamanho enquanto o multiplicador a diminui.

```
    return numerosRepetidos.includes(cpf)
}

function validaPrimeiroDigito(cpf) {
    let soma = 0;
    let multiplicador = 10;

    for (let tamanho = 0; tamanho < 9; tamanho++) {
        soma += cpf[tamanho] * multiplicador;
        multiplicador--
    }
```

<p>Este trecho de código retornará o final da multiplicação de cada dígito do CPF e também a soma total dessas multiplicações na variável soma. Abaixo do for vamos adicionar o valor final de soma, multiplicá-lo por 10 e dividi-lo por 11. Em seguida adicionaremos a condicional if para transformar em 0 os valores que resultarem em 10 ou 11. Também será adicionado um return comparando o valor final de soma com a posição 9 do CPF.</p>

```
    for (let tamanho = 0; tamanho < 9; tamanho++) {
        soma += cpf[tamanho] * multiplicador;
        multiplicador--
    }

    soma = (soma * 10) % 11;

    if (soma == 10 || soma == 11) {
        soma = 0;
    }

    return soma != cpf[9];
}
```

<p>Acessaremos novamente o início do arquivo valida-cpf.js e abaixo da função validaNumerosRepetidos acrescentaremos a função recém-criada validaPrimeiroDigito(cpf).</p>

```
export default function ehUmCPF(campo) 
    const cpf = campo.value.replace(/\.|-/g, "");
    validaNumerosRepetidos(cpf);
    validaPrimeiroDigito(cpf);
    // Trecho de código omitido
```

<p>Em seguida salvaremos o nosso código. Com a estrutura que montamos, podemos validar o primeiro dígito verificador de qualquer CPF.</p>

```
Exemplo: se utilizarmos o CPF "937.777.040-83" como base, a soma devolvida pelo for será 311. Portanto o resultado da operação 311 = (311 * 10) % 11; nos retornará o resultado 8. Neste caso, nosso CPF não entrará no if e será devolvido o valor 8.
```

<p>A seguir, incluiremos a verificação do segundo dígito, o que nos trará total confiança na validação do CPF inserido. Nos vemos lá!</p>

<h2>03. CPF: segundo dígito</h2>

<p>Já validamos o primeiro dígito verificador do nosso CPF, entretanto, o trabalho com este documento não acabará por aqui! Realizaremos agora a verificação do segundo dígito. Abriremos novamente o arquivo valida-cpf.js e codaremos juntos.</p>

<p>Faremos uma cópia da função validaPrimeiroDigito() disponível abaixo e vamos colá-la exatamente embaixo da primeira.</p>

```
function validaPrimeiroDigito(cpf) {
    let soma = 0;
    let multiplicador = 10;

    for (let tamanho = 0; tamanho < 9; tamanho++) {
        soma += cpf[tamanho] * multiplicador;
        multiplicador--
    }

    soma = (soma * 10) % 11;

    if (soma == 10 || soma == 11) {
        soma = 0;
    }

    return soma != cpf[9];
}
```

<p>Em seguida realizaremos algumas alterações nessa nova função.</p>

<p>
   - o nome validaPrimeiroDigito será alterado para validaSegundoDigito;
   - a variável let multiplicador terá o seu valor alterado de 10 para 11.
   - dentro do for vamos alterar a quantidade de repetições do laço de 09 para 10 vezes;
   - o return que comparava a posição [9] do cpf, agora utilizará a posição [10].
</p>

<p>A função validaSegundoDigito foi criada com a mesma lógica de sua antecessora. Apenas acrescentamos o primeiro dígito ao cálculo, pois este já terá sido verificado pela função anterior. Abaixo temos o seu código completo.</p>

```
function validaSegundoDigito(cpf) {
    let soma = 0;
    let multiplicador = 11;

    for (let tamanho = 0; tamanho < 10; tamanho++) {
        soma += cpf[tamanho] * multiplicador;
        multiplicador--
    }

    soma = (soma * 10) % 11;

    if (soma == 10 || soma == 11) {
        soma = 0;
    }

    return soma != cpf[10];
}
```

<p>Adicionaremos essa nova função no início do arquivo, no interior de export default function EhUmCPF() de forma a ligá-la com validaPrimeiroDigito(cpf) e validaNumerosRepetidos(cpf) através de uma condicional. Para isso apagaremos as funções adicionadas anteriormente: validaNumerosRepetidos(cpf), validaPrimeiroDigito(cpf) e console.log(validaNumerosRepetidos(cpf)).</p>

```
    validaNumerosRepetidos(cpf);
    validaPrimeiroDigito(cpf);
    console.log(validaNumerosRepetidos(cpf));
```

<p>Em seguida digitaremos um if que tratará de testar as três funções que criamos de uma vez só. Caso alguma delas não retornar true, imprimiremos a mensagem "Esse cpf não existe!", e caso contrário adicionaremos um else para imprimir a mensagem "Existe!".</p>

```
export default function ehUmCPF(campo) {
    const cpf = campo.value.replace(/\.|-/g, "");
    if (validaNumerosRepetidos(cpf) || validaPrimeiroDigito(cpf) || validaSegundoDigito(cpf)) {
        console.log("Esse cpf não existe!")
    } else {
            console.log("Existe!")
    }
}
```

<p>Salvaremos o nosso código e retornaremos ao Monibank pelo navegador. Dentro do campo CPF digitaremos um documento que não existe e clicaremos para fora. Neste momento a aba "Console" no interior de "Ferramentas do desenvolvedor" exibirá a mensagem "Esse cpf não existe!". Vamos testar também com um CPF do Gerador de CPFs disponível neste link. Quando ele for digitado será exibida na aba "Console" a mensagem "Existe!".</p>

<p>Todas as validações que criamos para o CPF estão funcionais, portanto podemos iniciar a etapa de validação de idade da pessoa usuária. Até lá!</p>

<h2>07. Validação idade</h2>

<p>O Monibank não aceita clientes menores de idade, portanto devemos criar uma validação que garanta que a pessoa cadastrada não seja menor de 18 anos.</p>

<p>O primeiro passo é criar um arquivo para esse código, pois conforme dito anteriormente, vamos trabalhar com um arquivo diferente para cada validação. Acessaremos o explorador do Visual Studio Code, clicaremos na pasta "js" e selecionaremos o ícone de "Novo Arquivo" na barra superior do explorador. Daremos a ele o nome valida-idade.js.</p>

<p>Em seu interior, criaremos a função principal do arquivo: ehMaiorDeIdade(), que recebe o valor de campo. Dentro das chaves adicionaremos a variável const dataNascimento que possuirá um new Date(), que por sua vez recebe o campo.value do campo "Data de nascimento" e o converte em um valor inteligível pelo Javascript. Em seguida verificaremos a conversão do valor de dataNascimento através um console.log.</p>

```
export default function ehMaiorDeIdade(campo) {
    const dataNascimento = new Date(campo.value);
    console.log(validaIdade(dataNascimento));
}
```

<p>Para que o console.log funcione, precisamos importar essa função no arquivo script.js. Acessaremos este arquivo no interior da pasta "js" através do explorador e importaremos ehMaiorDeIdade logo abaixo de ehUmCPF, na linha 2.</p>

```
import ehUmCPF from "./valida-cpf.js";
import ehMaiorDeIdade from "./valida-idade.js";
```

<p>Ainda no interior deste arquivo, no interior da seção verificaCampo(campo) e abaixo do primeiro if, adicionaremos um segundo que verificará se o campo possui o nome "aniversario" e se ele está vazio. Caso ambas as condições forem verdadeiras, ele chamará a função ehMaiorDeIdade() para aquele campo.</p>

```
function verificaCampo(campo) {
    if (campo.name == "cpf" && campo.value.length >= 11) {
        ehUmCPF(campo);
    }
    if (campo.name == "aniversario" && campo.value != "") {
        ehMaiorDeIdade(campo);
    }
}
```

<p>Acessaremos o navegador e incluiremos a minha data de nascimento no campo "Data de nascimento": 04/01/1999. Neste momento o Console exibe as informações dessa data convertidas em Javascript: Sun Jan 03 1999 22:00:00, o que significa que a nossa função está funcionando.</p>

<p>Retornando ao VS Code, acessaremos novamente o arquivo valida-idade.js e substituiremos o console.log pela função validaIdade() que por sua vez enviará o valor de dataNascimento. Em seguida criaremos um console.log para retornar o valor de validaIdade(dataNascimento).</p>

<p>Criaremos também a própria fuction validaIdade(), abaixo das chaves da seção ehMaiorDeIdade(campo). Esta função possuirá os seguintes elementos:</p>

<p>
    - a variável dataAtual que receberá a data do momento atual em que estamos;
    - a variável dataMais18 que receberá os parâmetros de ano, mês e dia da data de nascimento inserida no campo e adicionará a ela uo número 18. - Assim podemos saber em que ano aquela pessoa fez 18;
    - um return que verificará se data atual é maior ou igual a dataMais18, confirmando que a pessoa usuária já completou 18 anos.
</p>

```
export default function ehMaiorDeIdade(campo) {
    const dataNascimento = new Date(campo.value);
    validaIdade(dataNascimento);

    console.log(validaIdade(dataNascimento));
}

function validaIdade(data) {
    const dataAtual = new Date();
    const dataMais18 = new Date(data.getUTCFullYear() + 18, data.getUTCMonth(), data.getUTCDate());

    return dataAtual >= dataMais18;
}
```

<p>Retornaremos ao navegador. Se incluirmos a minha data de nascimento novamente no campo "Data de nascimento", o Console retornará true, pois eu sou maior de idade. Entretanto se alterarmos o ano para "2010", o Console retornará false, pois até aquele momento ela possui menos de 18 anos.</p>

<p>Conseguimos configurar a validação de maioridade, entretanto o sistema ainda não retorna nenhuma mensagem, somente true ou false. A seguir, lidaremos com mensagens customizadas para cada erro. Nos vemos lá!</p>

<h1>Módulo 04. Comunicando ao Usuário</h1>

<h2>02. Validity State</h2>

<p>É possível inserir mensagens customizadas para cada tipo de erro que acontecer nos inputs do nosso formulário. Entretanto, é importante entender como o Javascript detecta esses erros nos bastidores da aplicação.</p>

<p>Acessaremos o interior do arquivo script.js. Abaixo do segundo if no interior de verificaCampo(campo) incluiremos um console.log(campo.validity).</p>

```
function verificaCampo(campo) {
    if (campo.name == "cpf" && campo.value.length >= 11) {
        ehUmCPF(campo);
    }
    if (campo.name == "aniversario" && campo.value != "") {
        ehMaiorDeIdade(campo);
    }
    console.log(campo.validity);
}
```

<p>Salvaremos o código e retornaremos ao navegador, abrindo novamente a aba "Console" dentro das "Ferramentas do desenvolvedor", através do atalho "Ctrl + Shift + I".</p>

<p>Clicaremos no campo "Data de nascimento" e depois fora dele. Neste momento o Console retornará uma lista chamada ValidityState que exibe possíveis erros de validação que ocorrem automaticamente quando interagimos com esse formulário. Neste caso todos os elementos estão retornando false, menos o valueMissing, já que deixamos o campo sem nenhum valor preenchido.</p>

<p>Entre estes possíveis erros, existe um que segue uma lógica diferente: o valid. Se qualquer um dos outros atributos retornar true, ele retornará false, informando que temos um erro acontecendo no campo que o torna inválido. Caso contrário ele retornará true, o que validará o campo.</p>

<p>Se clicarmos no botão "Avançar" no final do formulário, será exibida no campo "Nome" a mensagem "Preencha este campo", padrão para quando o valueMissing for true. Vamos retirar esta mensagem que para nós é um pouco limitada retornando ao Vs Code e acessando novamente o script.js.</p>

<p>Dentro da seção camposDoFormulario.forEach, abaixo de campo.addEventListener adicionaremos outro campo.addEventListener que possuirá o valor "invalid" e uma variável evento que enviará por sua vez uma função seta para evento.preventDefault().</p>

```
camposDoFormulario.forEach((campo) => {
    campo.addEventListener("blur", () => verificaCampo(campo));
    campo.addEventListener("invalid", evento => evento.preventDefault())
})
```

<p>Salvaremos este código. Se retornarmos ao navegador e repetirmos o clique em "Avançar", a mensagem não será mais exibida mesmo com erros de preenchimento. Dessa forma, poderemos configurar as mensagens de validação e erro do zero. Faremos essas customizações no próximo vídeo. Nos vemos lá!</p>

<h2>04. Mensagens customizadas</h2>

<p>Já conhecemos diversos tipos de erro que podem ocorrer em nosso formulário através do Validity State. Entre eles, separaremos os erros que ocorrem com mais frequência.</p>

<p>Retornando à lista ValidityState que foi aberta no vídeo anterior através do Console do navegador, identificamos os seguintes erros como sendo os mais frequentes:</p>

<p>
    - valueMissing;
    - typeMismatch;
    - patternMismatch;
    - tooShort;
    - customError.
</p>

<p>Vamos acessar o arquivo script.js abaixo da seção camposDoFormulario.forEach e adicioná-los através da criação de uma lista const tiposDeErro.</p>

```
camposDoFormulario.forEach((campo) => {
    //Trecho de código omitido
})

const tiposDeErro = [
    'valueMissing',
    'typeMismatch',
    'patternMismatch',
    'tooShort',
    'customError'
]
```

<p>Por que selecionamos estes cinco tipos de erros? Eles representam as ações mais comuns no preenchimento de um formulário.</p>

<p>
    - o valueMissing ocorre quando deixamos o campo vazio;
    - o typeMismatch ocorre quando erramos o tipo de input no campo, como por exemplo, na inserção de um e-mail sem o símbolo @;
    - o patternMismatch ocorre especialmente no campo de CPF que possui um padrão de expressão regular. Se o input não segui-lo, este erro será ativado;
    - o tooShort está relacionado aos atributos minlength e maxLength que inserimos em diversos pontos do código. Ele serve para acusar quando os padrões de comprimento do input não forem atendidos;
    - o customError se refere a erros customizados, como nos casos em que inserimos as lógicas de validação ehUmCPF e ehMaiorDeIdade.
</p>

<p>Abaixo dessa lista de erros, criaremos mensagens customizadas para cada um deles. Para isso, devemos colar o código pronto com as mensagens de erro customizadas, disponível através deste link. Nele encontraremos a variável const mensagens onde criamos um objeto que possui propriedades cujos nomes correspondem a cada campo do nosso formulário: nome, email, rg, cpf, aniversario e termos. Cada um deles, por sua vez, recebe outro objeto que possui o nome dos possíveis erros e as respectivas mensagens que podem ser exibidas naquele campo.</p>

<p>Observação: as mensagens podem ser customizadas do jeito que quiser. Caso queira fazer alguma mudança, fique à vontade para tomar as rédeas do seu projeto e soltar a criatividade!</p>

<p>Já separamos os tipos de erro e criamos mensagens customizadas. A seguir, uniremos todas as informações e configuraremos a impressão de cada mensagem, conectando-as a seus respectivos erros. Nos vemos lá!</p>

<h2>05. Imprimindo mensagens</h2>

<p>Criamos uma lista reunindo todos os tipos de erros que podem ocorrer e outra lista com as mensagens customizadas para cada um deles. Vamos configurar a aplicação para que, ao ativarmos cada erro, a sua respectiva mensagem apareçam na tela.</p>

<p>Retornando ao código, ainda no arquivo script.js, no interior da função verificaCampo(campo) criaremos uma let mensagem recebendo um valor vazio, e depois substituiremos o comando console.log(campo.validity) por uma listatiposDeErro.forEach que executará uma função para cada item de erro. Em seu interior criaremos um if que observará se o campo.validity é true, e em caso positivo, o erro está ocorrendo. Incluiremos neste if a variável mensagem para receber uma mensagem de erro de dentro da lista mensagens[], identificando-a através do campo.name e do nome daquele erro específico. Em seguida imprimiremos o valor de mensagem no console.</p>

```
function verificaCampo(campo) 
    let mensagem = "";
    if (campo.name == "cpf" && campo.value.length >= 11) {
        ehUmCPF(campo);
    }
    if (campo.name == "aniversario" && campo.value != "") {
        ehMaiorDeIdade(campo);
    }
    tiposDeErro.forEach(erro => {
        if (campo.validity[erro]) {
            mensagem = mensagens[campo.name][erro];
            console.log(mensagem);
        }
    })
```

<p>Salvaremos o código e acessaremos o navegador, ainda com o Console aberto, para testar o código. Se clicarmos no campo Nome e em seguida clicarmos fora, o Console exibirá a mensagem "O campo de nome não pode estar vazio." Podemos ver, portanto, que o código está funcional.</p>

<p>No momento estamos imprimindo a mensagem somente no console, entretanto, queremos imprimi-la na tela. Para isso acessaremos o arquivo que representa o local em que devemos imprimir mensagens de erro: o abrir-conta-form.html.</p>

<p>Em seu interior verificaremos cada fieldset no qual existe um input name. Embaixo deste existe um span com a classe mensagem-erro — é nele que vamos inserir as mensagens de erro.</p>

<p>Exemplo: fieldset do campo "Nome":</p>

```
                <fieldset class="formulario__campo">
                    <label class="campo__etiqueta" for="nome">Nome</label>
                    <input name="nome" id="nome" class="campo__escrita" type="text" minlength="3" required />
                    <span class="mensagem-erro"></span>
                </fieldset>
```

<p>Copiaremos o trecho com o nome da classe: mensagem-erro e acessaremos novamente o arquivo script.js. Em seu interior vamos retornar à função verificaCampo(campo) e criar logo abaixo de tiposDeErro.forEach uma variável const mensagemErro que selecionará o span de mensagem-erro do nosso HTML através de um campo.parentNode.querySelector que por sua vez receberá o código que copiamos: mensagem-erro. Este comando selecionará somente o span do input mais próximo.</p>

<p>Em seguida, criaremos a variável const validadorDeInput que receberá um campo.checkValidity(). Este trecho checará se o campo é válido ou não. Adicionaremos também um if que imprimirá uma mensagem de erro caso o validadorDeInput retorne false, e em seguida um else que retornará um valor vazio caso o validadorDeInput retorne true.</p>

```
    tiposDeErro.forEach(erro => {
        if (campo.validity[erro]) {
            mensagem = mensagens[campo.name][erro];
            console.log(mensagem);
        }
    })
    const mensagemErro = campo.parentNode.querySelector('.mensagem-erro');
    const validadorDeInput = campo.checkValidity();

    if (!validadorDeInput) {
        mensagemErro.textContent = mensagem;
    } else {
        mensagemErro.textContent = "";
    }
```

<p>Os comandos que digitamos possibilitam que o sistema imprima as mensagens de erro padrão. Entretanto, queremos que ele imprima as mensagens customizadas. Para isso, acessaremos os arquivos valida-idade.js e valida-cpf.js, respectivamente. No interior das funções ehMaiorDeIdade e ehUmCPF de cada arquivo faremos as alterações abaixo:</p>

<p>- dentro de ehMaiorDeIdade substituiremos a função de verificação validaIdade por um if que verifica o validaIdade e recebe um parâmetro dataNascimento. Em seu interior adicionaremos um campo.setCustomValidity que receberá a nossa mensagem customizada: "A pessoa usuária não é maior de idade."</p>

```
export default function ehMaiorDeIdade(campo) {
    const dataNascimento = new Date(campo.value);
    if (!validaIdade(dataNascimento)) {
        campo.setCustomValidity('O usuário não é maior de idade');
    }
}
```

<p>- no interior de ehUmCPF, abaixo da seção const cpf = campo.value.replace, vamos deletar o console.log() dentro do if e também substituiremos todo a seção else por um campo.setCustomValidity que receberá a nossa mensagem customizada: "Este cpf não é válido."</p>

```
export default function ehUmCPF(campo) {
    const cpf = campo.value.replace(/\.|-/g, "");
    if (validaNumerosRepetidos(cpf) || validaPrimeiroDigito(cpf) || validaSegundoDigito(cpf)) {
        campo.setCustomValidity('Esse cpf não é válido');
    }
}
```

<p>Vamos entender o código? O customError só é ativado no momento em que o setCustomValidity não for false. Esta lógica precisava ser implementada manualmente, e para isso adicionamos o campo.setCustomValidity com um valor qualquer diretamente no ehUmCPF. Através da inserção deste valor o customError deixou de ser false, e portanto a mensagem pôde ser exibida.</p>

<p>A partir destas alterações, se retornarmos ao navegador, clicarmos no campo "Data de nascimento", preenchermos uma data menor do que 18 anos atrás e clicarmos fora, a aplicação retornará abaixo do campo a mensagem "O usuário é maior de idade" na cor vermelha. Caso a data gere um resultado maior do que 18, nenhuma mensagem será exibida.</p>

<p>Da mesma forma, se clicarmos no campo "CPF", adicionarmos um CPF válido copiado do site Gerador de CPFs e clicarmos fora, nenhuma mensagem será exibida. Entretanto, se inventarmos um CPF qualquer, a aplicação retornará abaixo do campo a mensagem "Esse cpf não é válido" na cor vermelha.</p>

<p>Por enquanto, se adicionarmos qualquer dado válido por cima de um dado inválido, a mensagem de erro permanecerá na tela. Para consertar esse problema, configuraremos a aplicação para redefinir o setCustomValidity() do campo. Para isso, retornaremos ao arquivo script.js e acessaremos a função verificaCampo(campo). Abaixo de let mensagem = "", adicionaremos um campo.setCustomValidity() que receberá um valor vazio.</p>

```
function verificaCampo(campo) 
    let mensagem = "";
    campo.setCustomValidity('');
    // Trecho de código omitido
```

<p>Salvaremos esse código e retornaremos ao navegador com o Console aberto. Adicionaremos no campo "CPF" um CPF inválido e clicaremos fora do campo. A mensagem de erro será exibida. Se, em seguida, adicionarmos um CPF válido, a mensagem de erro abaixo do campo desaparecerá.</p>

<p>Implementamos as verificações e fizemos a aplicação exibir as mensagens de erro na tela. A seguir, aprenderemos a enviar os dados do nosso formulário, simulando um cadastro. Até lá!</p>

<h2>07. localStorage</h2>

<p>Já lidamos com vários cenários em que a pessoa usuária poderia preencher dados incorretos nos campos do nosso formulário. Mas, e se chegássemos no cenário perfeito, no qual todos os dados fossem preenchidos corretamente? Como vamos lidar com esses dados e salvá-los em algum local?</p>

<p>Abriremos o Vs Code e acessaremos o arquivo abrir-conta-form.html. Em seu interior acessaremos o elemento form class="principal__formulario". Observaremos que a pessoa desenvolvedora que configurou esse HTML adicionou ao formulário um form, uma class e um data attribute chamado data-formulario. Vamos selecionar esse formulário por meio desses data attributes.</p>

<p>Fecharemos o arquivo HTML e voltaremos a acessar o script.js. Em seu interior, abaixo de const camposDoFormulario criaremos a variável const formulario que receberá um document.querySelector(). No interior deste último adicionaremos o data-formulario. Daremos "Enter" para descermos duas linhas e criaremos um formulario.addEventListener(). No interior dos parênteses adicionaremos um submit para o evento de envio e, que por sua vez será recolhido por um preventDefault().</p>

<p>No interior das chaves desse Event Listener adicionaremos uma listaRespostas que conterá a seguinte fórmula: "NOME_DO_CAMPO": e.target.elements["NOME_DO_CAMPO"].value. Adicionaremos uma linha desse comando para cada campo do formulário, substituindo o trecho "NOME_DO_CAMPO" por "nome", "email", "rg", "cpf" e "aniversario", respectivamente. A lista que criamos navegará pelo evento do formulário e selecionará o alvo e.target, os elements que possuem o nome daquele alvo, e também o seu value.</p>

<p>Abaixo das chaves de const listaRespostas criaremos um localStorage no qual adicionaremos um set.item, que possuirá como parâmetros o cadastro e um JSON.stringify() que converterá para JSON o nosso listaRespostas, tornando possível o salvamento dos dados do formulário.</p>

<p>Caso queira aprofundar seus conhecimentos sobre a propriedade localStorage, basta consultar a seção "Para saber mais: localStorage e DOM" disponível neste link, onde disponibilizamos algumas informações e links sobre esse assunto.</p>

<p>Também adicionaremos um window.location.href que redirecionará a pessoa usuária para a próxima etapa do formulário — a de reconhecimento facial, recebendo a rota desse arquivo: abrir-conta-form-2.html.</p>

```
const camposDoFormulario = document.querySelectorAll('[required]')
const formulario = document.querySelector('[data-formulario]');

formulario.addEventListener("submit", (e) => {
    e.preventDefault();

    const listaRespostas = {
        "nome": e.target.elements["nome"].value,
        "email": e.target.elements["email"].value,
        "rg": e.target.elements["rg"].value,
        "cpf": e.target.elements["cpf"].value,
        "aniversario": e.target.elements["aniversario"].value,
    }
    localStorage.setItem("cadastro", JSON.stringify(listaRespostas));

    window.location.href = "./abrir-conta-form-2.html";
})
```

<p>Salvaremos o código e testaremos no navegador. Na página do formulário, com a coluna "Ferramentas do desenvolvedor" aberta ao lado direito, digitaremos todos os campos de modo que sejam válidos, clicaremos no checkbox e depois no botão "Avançar". Nesse momento seremos redirecionados para a página de reconhecimento facial. Para descobrir onde esses dados foram salvos acessaremos o menu superior de "Ferramentas do desenvolvedor" e selecionaremos a aba "Aplicativo". Neste momento outra aba será aberta à esquerda. Nela localizaremos a opção "Armazenamento local" a qual possui a URL do nosso servidor local. Clicaremos nesta URL e visualizaremos na coluna principal de "Ferramentas do desenvolvedor" duas colunas denominadas "chave", cujo conteúdo é "cadastro" e "Valor", cujo interior armazena todas as informações preenchidas no formulário. Podemos constatar que os dados estão armazenados em nossa sessão local.</p>

<p>Completamos a primeira etapa. No próximo vídeo configuraremos a funcionalidade na qual será possível tirar fotografias do rosto e uniremos os dados dessa foto aos dados do formulário. Deixaremos bem completo o processo de cadastro do nosso Monibank. Nos vemos lá!</p>

<h1>Módulo 05. Capturando fotos</h1>

<h2>02. Iniciar câmera</h2>

<p>Chegamos na segunda etapa do cadastro de pessoas usuárias do nosso Monibank, que consiste na pessoa usuária ser capaz de tirar uma fotografia de si para completar o cadastro.</p>

<p>Rodaremos a página de reconhecimento facial no navegador, onde encontraremos as imagens e os títulos que já descrevemos anteriormente. Voltando ao Vs Code, acessaremos por meio do explorador a pasta "pages" e dentro dela clicaremos no arquivo abrir-conta-form-2.</p>

<p>Em seu interior podemos ver os elementos que compõem cada trecho da página e também duas divs denominadas formulario__camera e formulario__mensagem. Dentro da primeira temos os elementos video que representa a nossa câmera e button que representa o botão responsável por disparar a foto. Já dentro da segunda div temos um canvas onde nossa fotografia será armazenada, uma imagem de check e um texto que representam o sucesso da operação. Temos também um botão que nos enviará para a página de conclusão do cadastro.</p>

<p>Por que as duas divs não estão aparecendo na página? Eles foram ocultos pelo CSS, pois fazem parte de um ciclo de interação na página, onde devemos clicar em um elemento para que o outro seja exibido. Precisamos configurar esse ciclo com o Javascript.</p>

<p>Através do explorador da IDE selecionaremos a pasta "js". Nela criaremos um novo arquivo denominado camera.js. Em seu interior criaremos as novas variáveis botaoIniciarCamera, campoCamera e video nas quais adicionaremos, respectivamente, os data attributes abaixo, copiados do HTML:</p>

<p>
    - data-video-botao que representa o rosto sorridente;
    - data-camera que representa a câmera e
    - data-video que representa o vídeo da câmera em si.
</p>

<p>Cada um deles será inserido na nova variável por meio do document.querySelector().</p>

```
const botaoIniciarCamera = document.querySelector("[data-video-botao]");
const campoCamera = document.querySelector("[data-camera]");
const video = document.querySelector("[data-video]");COPIAR CÓDIGO
Com estes elementos criaremos o ciclo de interação.

Acessaremos o arquivo abrir-conta-form-2.html e abaixo do seu footer importaremos a câmera.

        // Trecho de código omitido
    </footer>
        <script src="../js/camera.js"></script>
</body>
```

<p>Retornando ao arquivo camera.js, criaremos a função que inicializa o vídeo, ativada pelo clique no botaoIniciarCamera. Para isso adicionaremos nesse botão um ouvinte de eventos (event listener) que receberá como parâmetros um click e uma async function(){}. Dentro das chaves dessa function adicionaremos uma const iniciarVideo que receberá o métodoawait navigator.mediaDevices.getUserMedia() que por sua vez possuirá a função de inicializar a câmera. Dentro dos parênteses, abriremos chaves e adicionaremos video: true, audio: false para solicitarmos somente o vídeo da câmera.</p>

<p>Abaixo da const iniciarVideo, ainda no interior da async function, adicionaremos ao botaoIniciarCamera um style.display = "nome" para que ele desapareça assim que a câmera for inicializada. Abaixo desse style.display adicionaremos outro dentro da câmera em si, que receberá o valor "block", permitindo dessa forma que a câmera apareça na tela. Abaixo deste segundo style.display adicionaremos um video.srcObject que receberá o iniciarVideo, configurando a tag de vídeo presente no HTML para receber como origem o navigator responsável por solicitar o acesso à câmera.</p>

```
botaoIniciarCamera.addEventListener('click', async function () {
    const iniciarVideo = await navigator.mediaDevices
        .getUserMedia({ video: true, audio: false });

    botaoIniciarCamera.style.display = "none";
    campoCamera.style.display = "block";

    video.srcObject = iniciarVideo;
});
```

<p>Todo esse código funciona no Javascript de maneira assíncrona, pois precisamos aguardar a pessoa usuária aceitar o acesso à câmera dela.</p>

<p>Dica: Caso você se interesse em saber mais sobre Javascript assíncrono, pode acessar e se inscrever no Curso de JavaScript: consumindo e tratando dados de uma API, disponível no site da Alura através deste link. Também indicamos o nosso Alura + sobre JavaScript assíncrono e Fetch, disponível neste link. Bons estudos!</p>

<p>Conseguimos executar o processo de inicialização da câmera. A seguir, precisamos configurar a aplicação para que uma foto seja tirada quando o botão for acionado, e que seja possível visualizá-la na tela. É um conhecimento novo e muito bacana! Nos vemos lá!</p>
