# avaliação

## validando cpf

O CPF, ou Cadastro de Pessoas Físicas, é um documento emitido pela Receita Federal do Brasil que serve para identificar os contribuintes brasileiros, tanto residentes no país quanto no exterior. Ele é essencial para diversas atividades, como abrir contas bancárias, declarar imposto de renda, realizar compras a crédito, entre outras.

O CPF é composto por 11 dígitos numéricos, geralmente formatados como `XXX.XXX.XXX-YY`, onde `XXX.XXX.XXX` são os números do CPF propriamente ditos e `YY` são os dígitos verificadores, usados para validar a autenticidade do número.

O algoritmo de validação do CPF calcula o primeiro dígito verificador a partir dos 9 primeiros dígitos do CPF, e em seguida, calcula o segundo dígito verificador a partir dos 9 (nove) primeiros dígitos do CPF, mais o primeiro dígito, obtido na primeira parte.

Para explicar bem o processo de validação, vai ser usado como exemplo o CPF fictício, mas válido : `111.444.777-35`.

## cálculo dos dígitos

### cálculo do primeiro dígito

Para validar um CPF, é preciso começar com o calculo do primeiro dígito verificador. Para isso, é preciso separar os 9 primeiros dígitos do CPF (111444777) e multiplicar cada um dos números, da esquerda para a direita por números decrescentes a partir do 10.

Veja a tabela abaixo :

> | Dígito CPF|| Multiplicador|| Resultado |
> | :----: | :----: | :----: | :----: | :----: |
> ||||||
> | `1` | * | `10` | = | `10` |
> | `1` | * | `9` | = | `9` |
> | `1` | * | `8` | = | `8` |
> | `4` | * | `7` | = | `28` |
> | `4` | * | `6` | = | `24` |
> | `4` | * | `5` | = | `20` |
> | `7` | * | `4` | = | `28` |
> | `7` | * | `3` | = | `21` |
> | `7` | * | `2` | = | `14` |
> ||||||

Cada dígito do CPF é multiplicado pelo respectivo número. Depois todos os resultados são somados :

> `10` + `9` + `8` + `28` + `24` + `20` + `28` + `21` + `14` = `162`

A partir do resultado obtido na soma, é realizada uma divisão por `11`. Esse cálculo irá gerar um quociente e um resto inteiros. Então, dividir `162` por `11` irá gerar um quociente igual a `14` e um resto igual `8`.

A partir desse resultado, é feita a seguinte avaliação :
- se o resto da divisão for `menor que 2`, então o primeiro dígito é igual a `zero`;
- se o resto da divisão for `maior ou igual a 2`, então o dígito verificador é igual a `11 menos o resto da divisão`;

No exemplo, o resto obitido foi oito, logo o primeiro dígito verificador é o onze menor o resto :

> `11 - 8 = 3`

O primeiro dígito verificador é `3`.

### cálculo do segundo dígito

Para calcular o segundo dígito, é necessário já saber qual é o primeiro digito calculado. O mesmo processo de multiplicação e soma terá que ser realizado, mas dessa vez é incluído o recém calculado primeiro dígito verificador ao final. E, em vez de iniciar a multiplicação em 10 e decrescer até o 2, é iniciado em `11` e decrescendo ainda até o 2.

Veja a tabela abaixo :

> | Dígito CPF|| Multiplicador|| Resultado |
> | :----: | :----: | :----: | :----: | :----: |
> ||||||
> | `1` | * | `11` | = | `11` |
> | `1` | * | `10` | = | `10` |
> | `1` | * | `9` | = | `9` |
> | `4` | * | `8` | = | `32` |
> | `4` | * | `7` | = | `28` |
> | `4` | * | `6` | = | `24` |
> | `7` | * | `5` | = | `35` |
> | `7` | * | `4` | = | `28` |
> | `7` | * | `3` | = | `21` |
> | `3` | * | `2` | = | `6` |
> ||||||

Novamente é efetuada a soma dos resultados da multiplicação :

> `11` + `10` + `9` + `32` + `28` + `24` + `35` + `28` + `21` + `6` = `204`

E novamente o total do somatório é dividido por onze para obter o quociente `18` e o resto `6` da divisão.

Uma vez conhecidos o resto e o quociente, o mesmo teste do resto é realizado :
- se o resto da divisão for `menor que 2`, então o segundo dígito é igual a `zero`;
- se o resto da divisão for `maior ou igual a 2`, então o dígito verificador é igual a `11 menos o resto da divisão`;

No exemplo, subtraindo 11 do resto resultará em :

> `11 - 6 = 5`

Logo, `5` é o segundo dígito verificador.

### validando os dígitos

Agora que ambos os dígitos são conhecidos (`3` e `5`), é possível validar o CPF.

Para isso, é necessário comparar os dígitos primeiro e segundo encontrados com o CPF a ser validado, o `111.444.777-35` deste exemplo. Se o primeiro dígito for igual ao penúltimo número do CPF e o segundo dígito for igual ao último número do CPF, então ele é válido. Se qualquer um deles for diferente, então o CPF é inválido.

Por exemplo :
- 111.444.777-35 é válido;
- 111.444.777-36 é inválido;
- 111.444.777-45 é inválido;

## cpfs sempre inválidos

Embora a validação funcione para todos os CPFs no formato esperado, alguns CPFs bem específicos são considerados **sempre** inválidos

São aqueles com dígitos repetidos, isto é, é composto de apenas um dígito repetido 11 vezes. Por exemplo :
- `111.111.111-11`
- `222.222.222-22`
- `333.333.333-33`,
- etc

Então, seu algoritmo deverá ignorar os CPFs com o padrão acima e avisar ao usuário de sua invalidade.

## entrada de dados

É muito importante para um validador de CPF ser capaz de receber o CPF do usuário e então retornar uma forma de aviso quando à sua validade.

Então,seu programa deverá pedir **vários** CPFs ao usuário.

Os formatos possíveis para um CPF digitado podem ser `XXX.XXX.XXX-YY`, `XXXXXXXXXYY`, `XXX.XXX.XXXYY`, etc. Não podem ser aceitos caracteres alfanuméricos e caracteres especiais, com exceção do ponto `.` e do traço `-`. Para interromper a digitação dos CPFs o usuário precisará digitar `sair` em vez de um CPF.

Após receber o CPF, seu programa deverá mostrar se o que foi digitado é válido ou inválido.

Alguns exemplos de mensagens :
- *O CPF digitato está em um formato inválido*;
- *Não digite letras no CPF*;
- *O CPF <cpf_digitado> é inválido!*, se ao menos um dos dígitos verificadores forem diferentes dos dois últimos números do CPF;
- *O CPF <cpf_digitado> é válido!*, se ambos os dígitos verificadores forem iguais dos dois últimos números do CPF;

O campo <cpf_digitado> deverá estar no formato `XXX.XXX.XXX-YY`, independente de como ele foi digitado pelo usuário.

## mensagens

Crie mensagens de boas vindas, encerramento e notificando se o CPF foi validado corretamente ou incorretamente.

## otimização

Use funções para otimizar seu programa.

Embora o código da soma dos dígitos do CPF e da validação dos dígitos verificadores possa ser feito em uma função cada, isso não será obrigatório para seu programa. Crie funções para deixar seu programa organizado e mais eficiente.

Seu programa deverá, **por hora**, possuir ao menos 4 funções.

## módulos

Para melhor organização do software, organize seu programa em ao menos 2 módulos. Um deles conterá as funções e variáveis de seu programa e o outro será o módulo principal, que ficará responsável pela execução do programa, chamado de `main.py`. Ele irá realizar o `import` do módulo auxiliar.

## testes

Para que um programa funcione corretamente, é necessário que haja uma bateria de testes. Para isso, o uso da variável `__name__` dentro de um módulo é imprescindível.

Crie uma lista de testes com diversos CPFs inválidos e válido para serem realizados quando o módulo auxiliar for chamado diretamente. Realize testes com todas as funções do seu código. Exiba mensagens informando quando o teste ocorrer conforme o esperado e quando acontece um erro imprevisto.

## tratando erros

Acontece muito de ocorrer uma interrupção da execução do programa por culpa de um erro imprevisto. Para evitar isso, use os comandos `try` e `except` para evitar que a execução seja interrompida.

Seu programa deverá executar e jamais ser interrompido por um erro inesperado. Use exceções **`específicas`** para bloquear as interrupções.

## arquivos

Arquivos são uma forma eficiente de armazenar informações por tempo indeterminado. Por conta disso, é necessário que sejam criados registros das tentativas de validação do CPF. Ambos deverão ser cumulativos, isto é, a cada execução do programa os novos registros devem ser adicionados ao final deles.

Seu programa deverá ter dois arquivos distintos.
- `erros.log` : o arquivo será responsável por armazenar a data e hora exatos do pedido de validação, o CPF digitado pelo usuário e uma mensagem sucinta informando o motido dele ter sido invalidado, conforme o exemplo;

    exemplos :
    ```log
    [16/08/2024 18:55:34.123456] asdf : caracter inválido
    [19/08/2024 18:21:34.123456] 111.444.777-315 : tamanho inválido
    [20/08/2024 19:32:34.123456] 123.456.799-87 : 1º dígito inválido
    [20/08/2024 07:44:34.123456] 111.444777-15 : 1º dígito inválido
    [21/08/2024 10:01:34.123456] 111.444.777-36 : 2º dígito inválido
    [22/08/2024 00:12:34.123456] 111.111.111-11 : dígitos repetidos
    ```

- `validos.json` : o arquivo será responsável por armazenar a data e hora exatos do pedido de validação, armazenar os CPFs validados e que tiveram seus dois dígitos verificados e aprovados, conforme o exemplo;

    exemplo :
    ```json
    {
        [
            {"data":"16/08/2024","hora":"07:44:34.123456","cpf_digitado": "111444.777-35","digito_1": 3,"digito_2": 5,"cpf_formatado": "111.444.777-35"},
            {"data":"30/08/2024","hora":"18:21:34.123456","cpf_digitado": "111.444.777-35","digito_1": 3,"digito_2": 5,  "cpf_formatado": "111.444.777-35"},
            {"data":"31/08/2024","hora":"18:42:34.123456","cpf_digitado": "11144477735","digito_1": 3,"digito_2": 5,"cpf_formatado": "111.444.777-35"}
        ]
    }
    ```

## classes

É muito importante organizar o código em classes.

Para isso, seu programa deverá possuir ao menos duas classes :
- a classe `Cpf` deverá ser responsável por guardar o CPF digitado pelo usuário, realizar as validações dos dígitos verificadores, retornar quando estivar válido / inválido;
- a classe `Arquivo` deverá ser responsável por receber as mensagens e salvá-las ou no arquivo `erros.log` ou no arquivo `validos.json`;
- todas funções criadas envolvendo o CPF deverão ser adaptadas para serem usadas através dos objetos da classe `Cpf`, enquanto que todas as funções criadas envolvendo a manipulação de arquivos deverão ser adaptadas para serem usadas através de objetos da classe `Arquivo`;

Seu módulo principal, o módulo `main.py`, deverá receber o CPF ditado e torná-lo uma instância da classe `Cpf`, para só então realizar todas as validações e verificações.

## interface

Linha de comando pode ser algo que os programadores estão acostumados, mas as pessoas comuns não.
Então, seu programa deverá apresentar uma interface gráfica para que a pessoa possa digitar o CPF em um campo e apertar um botão para validar. Depois, seu programa deverá informar ao usuário se o CPF digitade é válido ou não. Adicione um Menu, onde o usuário poderá escolher encerrar o programa por lá. Ao usar o Menu, uma mensagem deverá aparecer para o usuário se ele realmente deseja encerrar o programa.

## o que usar

> [!CAUTION]
> Apenas os conteúdos vistos em aula (que estão neste repositório) são permitidos para a realização do código.
> Se algum material fora deste repositório for usado, ***`TODO`*** o código será invalidado e o aluno estará sugeito à **recuperação**.

## checklist

Abaixo há uma lista de todos os pontos que devem ser realizados.
Lista essa que irá aumentar quando novos conteúdos forem apresentados em aula.

Lista :

Parte 1
- [ ] receber um CPF do usuário;
- [ ] validar o CPF digitado (só pode possuir números, pontos e traço);
- [ ] mostrar uma mensagem informando se o CPF está em formato inválido;
- [ ] encontrar o primeiro dígito verificador;
- [ ] usar o primeiro dígito encontrado para o cálculo do segundo dígito verificador;
- [ ] encontrar o segundo dígito verificador;
- [ ] comparar os dois dígitos encontrados com os dois últimos números do CPF;
- [ ] mostrar o CPF digitado no formato XXX.XXX.XXX-YY;
- [ ] mostrar uma mensagem informando se o CPF digitado é válido ou inválido;

Parte 2
- [ ] receber diversos CPFs do usuário sem interromper o programa;
- [ ] rejeitar CPFs com dígitos iguais;

Parte 3
- [ ] mensagem de boas vindas;
- [ ] função para receber e validar o CPF;
- [ ] função para calcular a soma dos dígitos verificadores (uma função para ambas as somas);
- [ ] função para realizar os testes dos dígitos verificadores (uma função para ambos os testes);
- [ ] mensagem ao finalizar;

Parte 4
- [ ] organização do código em pelo menos dois módulos;
- [ ] um módulo será de auxiliar, onde terá as funções e variáveis;
- [ ] o outro será o principal e deverá ser chamado de `main.py`, onde o programa será executado;

Parte 5
- [ ] use da variável `__name__` para casos de teste nos módulos auxiliares;
- [ ] uso dos blocos `try` e `except`;
- [ ] criação e armazenamento dos CPFs inválidos em `erros.log`;
- [ ] criação e armazenamento dos CPFs válidos em `validos.json`;

Parte 6
- [ ] crie a classe `Cpf`;
- [ ] crie a classe `Arquivo`;
- [ ] use ambas as classes para instanciar objetos a partir do módulo `main.py`;
- [ ] adicione a data e hora em cada validação do CPF com o módulo `datetime`;

Parte 7
- [ ] crie uma interface para seu programa com o Tkinter;
- [ ] use, pelo menos, um de cada Widgets `Label`, `Entry`, `Button` e `Menu`;
- [ ] use `messagebox` para informar ao usuário das validações;
- [ ] use `messagebox` para confirmar o encerramento do programa;
- [ ] coloque toda a parte da interface em um módulo separado chamado de `gui.py`;
- [ ] o módulo `main.py` ficará responsável por importar as classes do módulo auxiliar e a interface do `gui.py`;
- [ ] o módulo `main.py` será o módulo intermediário entre os módulos auxilar (das classes) e a interface;
