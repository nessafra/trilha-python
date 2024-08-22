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
- se o resto da divisão for `menor que 2`, então o primeiro dígito é igual a `zero`;
- se o resto da divisão for `maior ou igual a 2`, então o dígito verificador é igual a `11 menos o resto da divisão`;

No exemplo, subtraindo 11 do resto resultará em :

> `11 - 6 = 5`

Logo, `5` é o segundo dígito verificador.

### testando

Agora que ambos os dígitos são conhecidos (`3` e `5`), é possível validar o CPF.

Para isso, é necessário comparar os dígitos primeiro e segundo com o CPF a ser validado, o `111.444.777-35` deste exemplo. Se o primeiro dígito for igual ao penúltimo número do CPF e o segundo dígito for igual ao último número do CPF, então ele é válido. Se qualquer um deles for diferente, então o CPF é inválido.

Por exemplo :
- 111.444.777-35 é válido;
- 111.444.777-36 é inválido;

### o programa

> [!CAUTION]
> Apenas os conteúdos vistos em aula (que estão neste repositório) são permitidos para a realização do código.
> Se algum material fora deste repositório for usado, ***`TODO`*** o código será invalidado e o aluno estará sugeito à **recuperação**.

Seu programa, **por enquanto**, deverá pedir apenas um CPF ao usuário.

Os formatos possíveis para um CPF digitado podem ser `XXX.XXX.XXX-YY`, `XXXXXXXXXYY`, `XXX.XXX.XXXYY`, etc. Não podem ser aceitos caracteres alfanuméricos e caracteres especiais, com exceção do ponto `.` e do traço `-`.

Ao final, seu programa deverá mostrar uma das mensagens abaixo :
- O CPF digitato está em um formato inválido, caso tenha sido digitado letras;
- O CPF <cpf_digitado> é inválido, se os dígitos verificadores forem diferentes dos dois últimos números do CPF;
- O CPF <cpf_digitado> é válido, se os dígitos verificadores forem iguais dos dois últimos números do CPF;

O campo <cpf_digitado> deverá estar no formato `XXX.XXX.XXX-YY`, independente do formato digitado pelo usuário.

#### checklist

Abaixo há uma lista de todos os pontos que devem ser realizados.
Lista essa que irá aumentar quando novos conteúdos forem apresentados em aula.

Lista :
- [ ] receber um CPF do usuário;
- [ ] validar o CPF digitado (só pode possuir números, pontos e traço);
- [ ] mostrar uma mensagem informando se o CPF está em formato inválido;
- [ ] encontrar o primeiro dígito verificador;
- [ ] usar o primeiro dígito encontrado para o cálculo do segundo dígito verificador;
- [ ] encontrar o segundo dígito verificador;
- [ ] comparar os dois dígitos encontrados com os dois últimos números do CPF;
- [ ] mostrar o CPF digitado no formato XXX.XXX.XXX-YY;
- [ ] mostrar uma mensagem informando se o CPF digitado é válido ou inválido;
