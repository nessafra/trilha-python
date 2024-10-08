Índice

1. [principais conceitos da poo](#principais-conceitos-da-poo)
1. [benefícios da poo](#benefícios-da-poo)
1. [comando `class`](#comando-class)
1. [método `__init__`](#método-__init__)
1. [atributos](#atributos)
    1. [atributos de instância](#atributos-de-instância)
    1. [atributos de classe](#atributos-de-classe)
1. [métodos de instância](#métodos-de-instância)
1. [exercícios](#exercícios)
1. [métodos mágicos](#métodos-mágicos)
1. [método `__str__`](#método-__str__)
1. [método `__repr__`](#método-__repr__)
1. [`__str__` vs `__repr__`](#__str__-vs-__repr__)
1. [exercícios `__str__` e `__repr__`](#exercícios-__str__-e-__repr__)

# programação orientada a objetos

A **Programação Orientada a Objetos (POO)** é um paradigma de desenvolvimento de software que organiza o código em torno de **objetos**, em vez de funções e procedimentos. Esses objetos são instâncias de **classes** (representações abstratas de entidades do mundo real ou de conceitos dentro do sistema), que encapsulam tanto os **dados** (atributos) quanto as **funções** (métodos) que operam sobre esses dados.

## principais conceitos da poo

1. **classe** : uma classe é um modelo ou template que define a estrutura e o comportamento de um conjunto de objetos semelhantes. Ela atua como um molde para criar objetos, especificando os atributos (dados) que cada objeto terá e os métodos (funções) que cada objeto poderá executar.

1. **objeto** : um objeto é uma instância de uma classe. É uma entidade concreta criada a partir do modelo definido pela classe, possuindo seus próprios valores para os atributos e a capacidade de executar os métodos definidos na classe.

1. **encapsulamento** : o encapsulamento é o princípio de ocultar os detalhes internos de um objeto e fornecer uma interface pública para interagir com ele. Isso protege os dados do objeto de acessos e modificações indesejadas, permitindo que o objeto gerencie seu próprio estado de forma controlada.

1. **herança** : a herança é um mecanismo que permite criar novas classes (subclasses ou classes derivadas) a partir de classes existentes (superclasses ou classes base). A subclasse herda os atributos e métodos da superclasse, podendo adicionar novos atributos e métodos ou sobrescrever os existentes, promovendo a reutilização de código e a organização hierárquica das classes.

1. **polimorfismo** : o polimorfismo é a capacidade de objetos de diferentes classes responderem à mesma mensagem (chamada de método) de maneiras diferentes. Isso permite que o código seja mais flexível e adaptável, tratando objetos de diferentes classes de forma uniforme através de uma interface comum.

1. **abstração** : a abstração é o processo de focar nos aspectos essenciais de um objeto e ignorar os detalhes irrelevantes. Isso permite criar modelos simplificados e gerenciáveis de entidades complexas, facilitando o entendimento e a manipulação do sistema.

## benefícios da poo

* **modularidade** : a poo promove a organização do código em módulos (classes) coesos e independentes, facilitando a manutenção e a evolução do sistema;
* **reusabilidade** : a herança e o polimorfismo permitem reutilizar código existente em diferentes contextos, aumentando a produtividade e reduzindo a redundância;
* **flexibilidade** : o encapsulamento e o polimorfismo tornam o código mais flexível e adaptável a mudanças, facilitando a manutenção e a extensão do sistema;
* **escalabilidade** : a poo facilita o desenvolvimento de sistemas complexos e de grande porte, permitindo dividir o problema em partes menores e gerenciáveis;
* **manutenibilidade** : a organização modular e a reutilização de código tornam o sistema mais fácil de manter e atualizar ao longo do tempo;

## comando `class`

O comando `class` em Python é usado para definir uma **classe**.

### sintaxe básica

O comando `class` cria uma nova classe em Python. A sintaxe é a seguinte:

```python
class NomeDaClasse:
    pass
```

Aqui, `NomeDaClasse` é o nome da classe que se está criando. O comando `pass` é um placeholder que significa "não faça nada". Ele é temporariamente usado quando você quer definir uma classe sem especificar nenhum detalhe ainda.

Exemplo:

```python
class Carro:
    pass
```

Neste exemplo, foi criada uma classe chamada `Carro`, mas ela ainda não tem nenhuma característica ou comportamento.

### instâncias

Depois de definir uma classe, é possível criar **instâncias** dessa classe. Uma instância é um objeto criado a partir de uma classe, ou seja, um "exemplar" específico dessa classe.

Usando o exemplo da classe `Carro`, é possível criar uma instância da seguinte forma :

```python
meu_carro = Carro()
```

Aqui, `meu_carro` é uma instância da classe `Carro`. Ele é um objeto real, enquanto a classe `Carro` é apenas o molde ou a definição. É possível criar várias instâncias da mesma classe :

```python
carro1 = Carro()
carro2 = Carro()
```

Aqui, `carro1` e `carro2` são duas instâncias diferentes da mesma classe `Carro`. Elas compartilham a mesma estrutura (porque vêm da mesma classe), mas são objetos separados e podem ter suas próprias características.

### classe vs objeto

- **classe** : é uma definição ou molde, como uma receita de bolo ou a planta de um prédio. Ela descreve como os objetos devem ser, mas não é o objeto em si.
- **objeto (ou instância)** : é o resultado concreto criado a partir da classe. Quando se usa a classe para criar algo real, isso é chamado de objeto ou instância.

### exemplo no mundo real

Pense em uma classe como um **plano de uma casa**. O plano define o número de quartos, banheiros, o tamanho da cozinha, etc. Mas ele não é uma casa de verdade.

- a classe é o plano da casa;
- as casas construídas com base nesse plano são os objetos (ou instâncias);

Pode-se construir várias casas usando o mesmo plano, e cada casa será uma instância diferente, embora todas sigam o mesmo formato geral definido no plano.

## método `__init__`

O `__init__` é um **método especial** (também chamado de **método mágico**) em Python. Ele é o **construtor** de uma classe e é responsável por **inicializar** os atributos de uma instância de uma classe assim que essa instância é criada.

Quando se cria uma instância de uma classe, o Python chama automaticamente o método `__init__` para configurar essa nova instância. Embora o `__init__` pareça um método comum, ele tem uma função especial de configurar os atributos iniciais do objeto.

O `__init__` é definido dentro de uma classe da seguinte maneira:

```python
class NomeDaClasse:
    def __init__(self, parametros):
        # inicializa os atributos da instância
```

- o primeiro parâmetro de `__init__` é sempre `self`, que representa a instância da classe; ele é um opcional obrigatório e permite acessar os atributos e métodos dessa instância;
- além de `self`, ainda é poissível passar outros parâmetros ao método `__init__` para inicializar os atributos da instância com valores personalizados;

- Exemplo simples :

```python
class Carro:
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
```

Aqui :

- o método `__init__` recebe `marca` e `modelo` como parâmetros e os usa para definir os atributos `self.marca` e `self.modelo` da instância;
- o `self` refere-se à instância que está sendo criada, e os valores passados ao método `__init__` (como `marca` e `modelo`) são usados para inicializar essa instância;

Quando um objeto da classe `Carro` é criado, o Python executa automaticamente o método `__init__`.

```python
carro1 = Carro('Toyota', 'Corolla')
carro2 = Carro('Honda', 'Civic')
```

- para `carro1`, o `__init__` vai definir `self.marca = 'Toyota'` e `self.modelo = 'Corolla'`;
- para `carro2`, o `__init__` vai definir `self.marca = 'Honda'` e `self.modelo = 'Civic'`;

### o construtor de uma classe

Em Python, o método `__init__` é frequentemente chamado de **construtor** da classe, embora tecnicamente o construtor real seja o método `__new__`. No entanto, o `__init__` é o método que **inicializa** o objeto após a criação.

- o construtor, no sentido prático do termo em Python, é o responsável por **preparar** o objeto recém-criado, atribuindo valores iniciais aos seus atributos;

O fluxo de criação de uma instância de classe pode ser descrito assim :

1. o Python chama o método `__new__` para **criar** uma nova instância da classe;
1. em seguida, chama o método `__init__` para **inicializar** os atributos dessa instância;

Para a maioria dos desenvolvedores, o `__init__` é o que importa, pois é onde se define o estado inicial de um objeto. É nele que os **atributos de instância** são configurados.

## atributos

Os **atributos** são variáveis que armazenam informações sobre um objeto. Eles definem as propriedades e o estado de uma instância de uma classe.

Existem dois tipos principais de atributos em Python :

- **atributos de instância**
- **atributos de classe**

### atributos de instância

Os **atributos de instância** são variáveis que pertencem a uma instância específica de uma classe. Cada instância de uma classe pode ter seus próprios valores para esses atributos, permitindo que objetos diferentes da mesma classe tenham características únicas.

Os atributos de instância são definidos dentro do método `__init__` usando a referência `self`. O `self` permite associar os valores passados como parâmetros ao objeto que está sendo criado.

- Exemplo de Atributos de Instância :

No exemplo abaixo, foi criada uma classe `Carro` com atributos de instância como `marca`, `modelo`, e `ano` :

```python
class Carro:
    def __init__(self, marca, modelo, ano):
        self.marca = marca  # atributo de instância
        self.modelo = modelo  # atributo de instância
        self.ano = ano  # atributo de instância
```

Aqui :
- `self.marca`, `self.modelo`, e `self.ano` são os **atributos de instância**;
- Cada instância da classe `Carro` terá seus próprios valores para esses atributos;

Quando se cria diferentes instâncias, cada uma terá seus próprios valores para `marca`, `modelo` e `ano` s:

```python
carro1 = Carro('Toyota', 'Corolla', 2020)
carro2 = Carro('Honda', 'Civic', 2019)

print(carro1.marca)  # Toyota
print(carro2.modelo)  # Civic
print(carro1.ano)  # 2020
```

- o objeto `carro1` terá os atributos `marca='Toyota'`, `modelo='Corolla'`, e `ano=2020`;
- o objeto `carro2` terá os atributos `marca='Honda'`, `modelo='Civic'`, e `ano=2019`;

Esses valores são **específicos** para cada instância de `Carro`, e podem ser diferentes para cada objeto criado.

### atributos de classe

Os **atributos de classe** são compartilhados por **todas** as instâncias de uma classe. Eles são definidos diretamente dentro da classe e fora de qualquer método. Todos os objetos dessa classe acessam e compartilham o mesmo valor para esses atributos, a menos que sejam sobrescritos.

```python
class Carro:
    rodas = 4  # atributo de classe, compartilhado por todas as instâncias

    def __init__(self, marca, modelo, ano):
        self.marca = marca  # atributo de instância
        self.modelo = modelo  # atributo de instância
        self.ano = ano  # atributo de instância
```

Aqui, `rodas` é um **atributo de classe**. Ele é o mesmo para todas as instâncias da classe `Carro` :

```python
carro1 = Carro('Toyota', 'Corolla', 2020)
carro2 = Carro('Honda', 'Civic', 2019)

print(carro1.rodas)  # 4
print(carro2.rodas)  # 4
```

Se um dos objetos mudar o valor de `rodas`, ele só afetará esse objeto se for sobrescrito em nível de instância:

```python
carro1.rodas = 6  # Muda o número de rodas apenas para carro1
print(carro1.rodas)  # 6
print(carro2.rodas)  # 4 (não foi alterado)
```

### atributos de instância vs atributos de classe

Como mencionado antes, os **atributos de instância** pertencem a cada objeto separadamente, enquanto os **atributos de classe** pertencem à classe em si e são compartilhados por todas as instâncias.

```python
class Carro:
    rodas = 4  # atributo de classe (compartilhado por todas as instâncias)

    def __init__(self, marca, modelo, ano):
        self.marca = marca  # atributo de instância (específico para cada instância)
        self.modelo = modelo  # atributo de instância
        self.ano = ano  # atributo de instância
```

Aqui:
- `rodas` é um **atributo de classe**. Todos os carros (instâncias) terão 4 rodas, a menos que seja explicitamente alterado.
- `marca`, `modelo` e `ano` são **atributos de instância**. Eles podem variar de um carro para outro.

## métodos de instância

Os **métodos de instância** são funções definidas dentro de uma classe que operam sobre uma instância específica dessa classe. Ou seja, eles têm acesso e podem modificar os **atributos de instância** — valores únicos para cada objeto criado a partir da classe.

Cada método de instância, por convenção, tem o parâmetro `self` como seu primeiro argumento. O `self` se refere à instância específica da classe sobre a qual o método está sendo chamado e permite que você acesse ou modifique seus atributos.

### estrutura

```python
class MinhaClasse:
    def __init__(self, valor):
        self.valor = valor  # atributo de instância

    def metodo_instancia(self):
        print(f"O valor atual é: {self.valor}")
```

Aqui, `metodo_instancia` é um método de instância. Quando chamamos esse método em uma instância de `MinhaClasse`, ele acessa o atributo `valor` daquela instância em particular.

- **`self`**: É a referência à instância atual da classe. Sempre deve ser o primeiro parâmetro em qualquer método de instância, mas não é necessário passá-lo explicitamente ao chamar o método; o Python o gerencia automaticamente. Ele permite que o método acesse e modifique os atributos e outros métodos de instância.

- **Método de instância**: Qualquer função dentro de uma classe que tem `self` como o primeiro parâmetro.

### exemplos

#### exemplo 1: criando e chamando um método de instância

```python
class Pessoa:
    def __init__(self, nome, idade):
        self.nome = nome  # atributo de instância
        self.idade = idade  # atributo de instância

    def saudacao(self):  # método de instância
        print(f"Olá, meu nome é {self.nome} e tenho {self.idade} anos.")
```

Aqui, o método de instância `saudacao` usa `self` para acessar os atributos `nome` e `idade`.

```python
# Criando uma instância de Pessoa
pessoa1 = Pessoa("Ana", 30)
pessoa1.saudacao()  # Chama o método saudacao
```

**Saída:**

```
Olá, meu nome é Ana e tenho 30 anos.
```

- o método `saudacao` foi chamado na instância `pessoa1`. Ele acessa os atributos `nome` e `idade` através do `self`;

#### exemplo 2: modificando atributos com métodos de instância

```python
class Carro:
    def __init__(self, marca, modelo):
        self.marca = marca  # atributo de instância
        self.modelo = modelo  # atributo de instância

    def mudar_modelo(self, novo_modelo):  # método de instância
        self.modelo = novo_modelo  # Modificando o atributo de instância
        print(f"O modelo do carro foi atualizado para {self.modelo}.")

# Criando uma instância de Carro
meu_carro = Carro("Toyota", "Corolla")
meu_carro.mudar_modelo("Camry")  # Modifica o modelo
```

**Saída:**

```
O modelo do carro foi atualizado para Camry.
```

- o método `mudar_modelo` foi usado para modificar o valor do atributo `modelo` da instância `meu_carro`;

#### exemplo 3: métodos de instância que executam cálculos

```python
class Retangulo:
    def __init__(self, largura, altura):
        self.largura = largura  # atributo de instância
        self.altura = altura  # atributo de instância

    def calcular_area(self):  # método de instância
        return self.largura * self.altura

# Criando uma instância de Retangulo
meu_retangulo = Retangulo(5, 3)
area = meu_retangulo.calcular_area()  # Chamando o método calcular_area
print(f"A área do retângulo é: {area}")
```

**Saída:**

```
A área do retângulo é: 15
```

- aqui, o método `calcular_area` retorna a área do retângulo multiplicando os atributos `largura` e `altura`;

### importância dos métodos de instância

1. **Encapsulamento** : eles permitem encapsular o comportamento específico de uma instância dentro da classe; isso mantém a lógica organizada e evita que o código seja espalhado em várias partes do programa;

1. **Acesso e Modificação de Atributos** : métodos de instância podem acessar, modificar e retornar os valores dos atributos de uma instância específica, facilitando o gerenciamento do estado interno do objeto;

1. **Reutilização** : os métodos de instância permitem reutilizar o comportamento, pois pode criar várias instâncias de uma classe e usar os mesmos métodos em diferentes objetos;

#### exemplo 4: métodos que combinam atributos

```python
class ContaBancaria:
    def __init__(self, titular, saldo):
        self.titular = titular
        self.saldo = saldo  # atributo de instância

    def depositar(self, valor):  # método de instância
        self.saldo += valor
        print(f"Depósito de {valor} realizado com sucesso. Saldo atual: {self.saldo}")

    def sacar(self, valor):  # método de instância
        if valor > self.saldo:
            print("Saldo insuficiente!")
        else:
            self.saldo -= valor
            print(f"Saque de {valor} realizado com sucesso. Saldo atual: {self.saldo}")

# Criando uma instância de ContaBancaria
minha_conta = ContaBancaria("João", 1000)
minha_conta.depositar(500)  # Adiciona dinheiro na conta
minha_conta.sacar(200)  # Remove dinheiro da conta
```

**Saída:**

```
Depósito de 500 realizado com sucesso. Saldo atual: 1500
Saque de 200 realizado com sucesso. Saldo atual: 1300
```

- o método `depositar` modifica o saldo da instância `minha_conta`, e o método `sacar` verifica se há saldo suficiente antes de realizar o saque;

### diferenciando métodos de instância de outros tipos de métodos

Em Python, existem três tipos principais de métodos em classes:

1. **métodos de instância** : já discutidos, são os mais comuns e operam em instâncias individuais de uma classe;

1. **métodos de classe** : usam o decorador `@classmethod` e recebem a própria classe como primeiro argumento, em vez de uma instância;

1. **métodos estáticos** : usam o decorador `@staticmethod` e não recebem nem a instância nem a classe como parâmetro. são usados quando o comportamento do método não depende da instância ou da classe;

Os métodos de **classe** e **estátivco** serão vistos posteriormente.

## exercícios

<details>
<summary>Lista de Exercícios</summary>

1. Exercícios sobre o Método `__init__`
    1. **Classe simples com `__init__`** : Crie uma classe `Animal` com o método `__init__` que inicialize o atributo `especie`.
    1. **Múltiplos parâmetros no `__init__`** : Crie uma classe `Livro` com o método `__init__` que receba os parâmetros `titulo` e `autor`.
    1. **Parâmetros padrão no `__init__`** : Crie uma classe `Produto` com o método `__init__`, onde o atributo `preco` tenha um valor padrão de 100.
    1. **Inicializando listas no `__init__`** : Crie uma classe `Estudante` com o método `__init__` que inicialize o atributo `notas` como uma lista vazia.
    1. **Modificando o `__init__`** : Modifique a classe `Estudante` do exercício anterior para permitir passar uma lista de notas como parâmetro no método `__init__`.
    1. **Verificação no `__init__`** : Crie uma classe `Pessoa` com o método `__init__` que receba a `idade` e garanta que a idade seja sempre maior que 0.
    1. **Atributo opcional no `__init__`** : Crie uma classe `Computador` que tenha um atributo opcional `marca`, cujo valor padrão seja `"Genérica"` no `__init__`.
    1. **Exibindo valores no `__init__`** : Crie uma classe `Filme` e, no método `__init__`, exiba o título do filme assim que a instância for criada.
    1. **Usando variáveis locais dentro do `__init__`** : Crie uma classe `Carro` com os atributos `marca` e `modelo`, onde o método `__init__` use variáveis locais para armazenar os parâmetros antes de inicializar os atributos de instância.
    1. **Criando instâncias dentro do `__init__`** :  Crie uma classe `Equipe` que, no método `__init__`, crie uma lista de membros (strings) fornecida como parâmetro.
1. Exercícios sobre Atributos de Instância
    1. **Acessando atributos de instância** :  Crie uma classe `Aluno` com os atributos de instância `nome` e `idade`. Crie um objeto e imprima o valor de seus atributos.
    1. **Modificando atributos de instância** :  Crie uma classe `Funcionario` com o atributo `salario`. Crie um objeto e imprima o valor de seus atributos.
    1. **Atributos dependentes de outros** :  Crie uma classe `Circulo` com os atributos `raio` e `area`, onde o `area` seja calculado no método `__init__` a partir do `raio`.
    1. **Atributos com valores fornecidos pelo usuário** :  Crie uma classe `Carro` com os atributos `marca` e `ano`. Permita que o usuário forneça os valores desses atributos ao criar a instância.
    1. **Lista de atributos de instância** :  Crie uma classe `Biblioteca` com um atributo `livros`, que seja uma lista de livros (strings) fornecida no método `__init__`.
    1. **Adicionando elementos a um atributo de instância** :  Crie uma classe `CestaDeCompras` com um atributo `produtos` (uma lista vazia). Peça ao usuário diversos itens que são adicionados em `produtos`.
    1. **Atributos de instância como contadores** :  Crie uma classe `Contador` com um atributo `valor`, que seja inicializado como 0 no método `__init__`. Peça para o usuário um número e incremente `valor` até o número escolhido pelo usuário.
    1. **Atributos de instância dependentes de condições** :  Crie uma classe `Candidato` com os atributos `nome` e `aprovado`. Se a nota for maior ou igual a 60, o atributo `aprovado` deve ser `True`, caso contrário, `False`.
    1. **Atributos de instância com valores calculados** :  Crie uma classe `Viagem` com os atributos `distancia` e `tempo`. Adicione um atributo `velocidade_media` que seja calculado dividindo a distância pelo tempo.
    1. **Atributos de instância inicializados como objetos** :  Crie uma classe `Casa` com um atributo de instância `proprietario`, que seja inicializado como uma instância de uma classe `Pessoa`.
1. Exercícios sobre Atributos de Classe
    1. **Atributo de classe simples** :  Crie uma classe `Pessoa` com um atributo de classe `especie` cujo valor seja `"Humano"`.
    1. **Acessando um atributo de classe** :  Crie uma classe `Carro` com o atributo de classe `rodas` igual a 4. Crie uma instância da classe e acesse o valor do atributo `rodas`.
    1. **Modificando um atributo de classe** :  Crie uma classe `Empresa` com um atributo de classe `empregados`. Modifique o valor desse atributo para 50 fora da classe.
    1. **Atributos de classe com valores dinâmicos** :  Crie uma classe `Banco` com o atributo de classe `taxa_juros`. Crie duas instâncias da classe e veja como o atributo de classe pode ser acessado e modificado globalmente.
    1. **Atributos de classe e instância com o mesmo nome** :  Crie uma classe `Animal` com um atributo de classe `especie` e um atributo de instância `especie`. Crie uma instância e veja qual valor prevalece ao acessá-los.
    1. **Contando o número de instâncias de uma classe** :  Crie uma classe `Aluno` com um atributo de classe `numero_de_alunos` que é incrementado sempre que uma nova instância for criada.
    1. **Atributo de classe com valor compartilhado** :  Crie uma classe `Universidade` com o atributo de classe `pais` igual a `"Brasil"`. Verifique que todas as instâncias dessa classe compartilham esse atributo.
    1. **Atributo de classe e `__init__`** :  Crie uma classe `Livro` com um atributo de classe `numero_de_livros` e incremente esse valor sempre que um novo livro for criado.
    1. **Verificando se o atributo é de instância ou de classe** :  Crie uma classe `Fruta` com um atributo de classe `tipo` e um atributo de instância `cor`. Verifique todos os valores dos atributos.
    1. **Atributos de classe versus instância** :  Crie uma classe `Celular` com um atributo de classe `tecnologia` e um atributo de instância `modelo`. Crie uma instância e veja como os atributos de classe e instância coexistem e podem ser acessados separadamente.
1. Exercícios sobre Atributos e Métodos de Instância
    1. **Criação e Exibição de Atributos** : Crie uma classe `Pessoa` com os atributos de instância `nome` e `idade`. Adicione um método `exibir_informacoes` que exiba esses atributos.
    1. **Atualização de Atributo via Método** : Crie uma classe `Carro` com os atributos `marca` e `modelo`. Adicione um método `mudar_modelo` que permita alterar o modelo do carro.
    1. **Cálculo com Atributos de Instância** : Crie uma classe `Retangulo` com os atributos `largura` e `altura`. Adicione um método `calcular_area` que retorne a área do retângulo.
    1. **Verificação de Atributos** : Crie uma classe `ContaBancaria` com os atributos `saldo` e `titular`. Adicione um método `verificar_saldo` que verifique se o saldo é suficiente para realizar uma operação.
    1. **Método que Retorna Atributos** : Crie uma classe `Livro` com os atributos `titulo` e `autor`. Adicione um método `informacoes_livro` que retorne uma string contendo o título e o autor do livro.
    1. **Modificação Condicional de Atributos** : Crie uma classe `Elevador` com o atributo `andar_atual`. Adicione métodos para `subir` e `descer` de andar, verificando se o andar atual está dentro dos limites de um prédio de 10 andares.
    1. **Método que Usa Vários Atributos** : Crie uma classe `Produto` com os atributos `preco` e `quantidade`. Adicione um método `calcular_total` que retorne o valor total do estoque com base no preço e quantidade.
    1. **Modificação e Exibição de Atributos** : Crie uma classe `Jogador` com os atributos `nome`, `pontos`. Adicione um método `ganhar_pontos` que aumente os pontos do jogador e exiba a nova pontuação.
    1. **Método que Modifica Atributos de Várias Instâncias** : Crie uma classe `Amigo` com o atributo `humor`. Adicione um método `animar_amigo` que mude o humor de todos os amigos de uma lista fornecida.
    1. **Método que Define Atributo com Base em Outros** : Crie uma classe `Circulo` com o atributo `raio`. Adicione um método `definir_diametro` que defina o diâmetro com base no raio.
    1. **Método que Modifica Mais de um Atributo** : Crie uma classe `ContaCorrente` com os atributos `saldo` e `limite`. Adicione um método `ajustar_limite` que ajuste o limite com base no saldo atual.
    1. **Método que Zera Atributos** : Crie uma classe `Jogador` com os atributos `nome` e `vidas`. Adicione um método `perder_vidas` que diminua o número de vidas e um método `resetar_vidas` que zere as vidas.
    1. **Método com Operações Matemáticas em Atributos** : Crie uma classe `Vendedor` com os atributos `vendas` e `comissao`. Adicione um método `calcular_comissao` que retorne o valor da comissão baseada nas vendas e uma porcentagem de comissão.
    1. **Método que Atualiza Listas como Atributos** : Crie uma classe `Turma` com um atributo `alunos` (uma lista). Adicione um método `adicionar_aluno` que permita adicionar novos alunos à turma.
    1. **Método que Lida com Atributos Complexos** : Crie uma classe `Funcionario` com o atributo `horas_trabalhadas`. Adicione um método `registrar_horas` que atualize o total de horas trabalhadas e calcule o pagamento com base em uma taxa por hora.
    1. **Método que Verifica e Modifica Atributos Condicionalmente** : Crie uma classe `CarroEletrico` com os atributos `bateria` (em %) e `autonomia`. Adicione um método `carregar_bateria` que aumenta a porcentagem da bateria e ajuste a autonomia com base na carga.
    1. **Método que Faz Comparações entre Atributos** : Crie uma classe `Produto` com os atributos `preco` e `desconto`. Adicione um método `aplicar_desconto` que subtraia o desconto do preço e retorne o preço final.
    1. **Método com Condicionais e Modificações** : Crie uma classe `Aluno` com os atributos `nome`, `notas` (uma lista de notas) e `media`. Adicione um método `calcular_media` que calcule a média das notas e defina se o aluno está aprovado ou não (média >= 7).
    1. **Método que Reconfigura um Atributo** : Crie uma classe `Veiculo` com o atributo `velocidade`. Adicione um método `ajustar_velocidade` que defina um novo valor para a velocidade e exiba a nova velocidade.
    1. **Método que Lida com Atributos Dinâmicos** : Crie uma classe `Cachorro` com os atributos `nome` e `energia`. Adicione métodos `brincar` (que reduz a energia) e `descansar` (que aumenta a energia), com o valor de energia nunca podendo ser menor que 0 ou maior que 100.

</details>

## métodos mágicos

**Métodos mágicos**, também conhecidos como **métodos dunder** (double underscore ou “duplo sublinhado”) em Python, são funções especiais que têm nomes com dois underscores no início e no fim, como `__init__`, `__str__`, `__len__`, entre outros. Esses métodos permitem que se defina comportamentos especiais para suas classes e instâncias, personalizando como os objetos se comportam em diferentes situações, como ao serem criados, comparados, adicionados, multiplicados, ou quando se tenta acessá-los de maneira específica.

A principal função desses métodos é permitir a **sobrecarga de operadores** (como `+`, `-`, `*`, `==`) e comportamentos integrados, ou seja, definir o que acontece quando se tenta utilizar operadores ou funções nativas em suas classes personalizadas. Eles também são usados em casos mais comuns, como :

- inicialização de objetos (`__init__`);
- representação de objetos como strings (`__str__`, `__repr__`);
- comparação entre objetos (`__eq__`, `__lt__`, etc.);
- implementação de coleções customizadas (`__getitem__`, `__setitem__`, etc.);

Esses métodos são automaticamente invocados em várias situações. Eles são um dos pilares da programação orientada a objetos em Python, proporcionando flexibilidade e personalização ao comportamento de objetos.

## método `__str__`

O método `__str__` é utilizado para **definir uma representação "legível" ou amigável** de um objeto. Esse método é chamado automaticamente quando usamos a função `print()` ou `str()` em uma instância de uma classe. A ideia por trás de `__str__` é gerar uma saída que seja útil para o **usuário final**, tornando o objeto mais fácil de entender.

**Exemplo**

```python
class Pessoa:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    def __str__(self):
        return f'{self.nome} tem {self.idade} anos.'

# criação de uma instância
pessoa1 = Pessoa("João", 30)

# utilizando print(), que chama __str__
print(pessoa1)  # saída : João tem 30 anos.
```

Neste exemplo, o método `__str__` foi implementado para que, quando a instância `pessoa1` for impressa, a saída seja uma frase legível para o usuário. Essa frase foi projetada para ser amigável e facilmente compreendida.

## método `__repr__`

O método `__repr__` é utilizado para fornecer uma **representação oficial e mais técnica do objeto**, muitas vezes com o objetivo de ser usada para **depuração** (debugging). A convenção é que `__repr__` tente retornar uma string que, se possível, possa ser utilizada para **recriar** o objeto (ou ao menos fornecer informações detalhadas sobre ele). Seu propósito principal é fornecer uma representação precisa para desenvolvedores.

**Exemplo**

```python
class Pessoa:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    def __repr__(self):
        return f'Pessoa(nome={self.nome!r}, idade={self.idade!r})'

# Criação de uma instância
pessoa1 = Pessoa("João", 30)

# Chamando diretamente __repr__
print(repr(pessoa1))  # saída : Pessoa(nome='João', idade=30)
```

Aqui, o método `__repr__` foi implementado para exibir os valores exatos dos atributos `nome` e `idade`, permitindo que a saída fosse mais detalhada e útil para entender o estado interno do objeto. Isso ajuda em depuração e, se possível, até recriar a instância de maneira precisa.

Dentro de uma `f-string` (formatted string literal), o `!r` é um especificador de formato que instrui o interpretador a usar a função `repr()` no valor da variável que o precede. Em outras palavras, ele garante que a representação da string do valor seja a mesma que seria obtida se chamasse explicitamente `repr()` nesse valor

## `__str__` vs `__repr__`

### finalidade

- **`__str__`** : é voltado para o usuário final, como ao exibir relatórios ou mensagens de log que os usuários verão. O foco está em fornecer uma saída legível e amigável. Ele pode omitir detalhes técnicos e ser mais descritivo;
- **`__repr__`** : é voltado para desenvolvedores. A intenção é fornecer uma representação detalhada e técnica do objeto, idealmente uma que possa ser usada para recriar o objeto. A saída de `__repr__` deve ser mais exata e explícita, especialmente em depuração;

### chamadas automáticas

- **`__str__`** : é chamado quando a função `print()` ou `str()` é usada;
- **`__repr__`** : é chamado quando você usa `repr()`, ou quando se simplesmente digita o nome da instância no prompt do interpretador Python. Se `__str__` não estiver definido, o Python usará `__repr__` como fallback, enquanto o contrário não é verdadeiro (ou seja, se `__repr__` não for definido, Python não utiliza `__str__` para depuração).;

### recriação do objeto

- **`__str__`** : não precisa, e geralmente não deve, tentar recriar o objeto. Seu objetivo é apenas fornecer uma descrição;
- **`__repr__`** : idealmente, a string retornada por `__repr__` deve conter informações suficientes para recriar o objeto;

### exemplo comparativo

Veja a classe `Carro` implementar ambos os métodos para comparar como eles funcionam

```python
class Carro:
    def __init__(self, marca, modelo, ano):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano

    def __str__(self):
        return f"{self.marca} {self.modelo} ({self.ano})"

    def __repr__(self):
        return f"Carro(marca={self.marca!r}, modelo={self.modelo!r}, ano={self.ano!r})"

# criando uma instância
carro1 = Carro("Toyota", "Corolla", 2020)

# usando print(), que chama __str__
print(carro1)  # saída : Toyota Corolla (2020)

# usando repr(), que chama __repr__
print(repr(carro1))  # saída : Carro(marca='Toyota', modelo='Corolla', ano=2020)
```

**Explicação**

- **`__str__`** : a saída `Toyota Corolla (2020)` é concisa e legível. Ela não se preocupa com o fato de que os valores de `marca`, `modelo` e `ano` são strings. Isso é o que um usuário final esperaria ver ao visualizar as informações do carro.

- **`__repr__`** : a saída `Carro(marca='Toyota', modelo='Corolla', ano=2020)` é mais técnica. Ela exibe os valores dos atributos entre aspas e no formato de uma chamada de construtor, facilitando o entendimento do estado interno do objeto. Essa saída seria útil para um desenvolvedor que está inspecionando o objeto durante a depuração.

### em suma

- **`__str__`**:
    - imprimir informações para o usuário final;
    - gerar relatórios;
    - criar uma saída amigável para logs ou interfaces de usuário;

- **`__repr__`**:
    - durante a depuração, para ver os detalhes técnicos do objeto;
    - para testar como os atributos de uma instância foram configurados;
    - em ambientes de desenvolvimento, como ao inspecionar o objeto no terminal do python;

## exercícios `__str__` e `__repr__`

<details>
<summary>Lista de Exercícios</summary>

1. 10 Exercícios para o Método `__str__`
    1. Crie uma classe `Livro` que tenha os atributos `titulo`, `autor` e `ano_publicacao`. Implemente o método `__str__` para que ele retorne uma string no formato: `"Título: <titulo>, Autor: <autor>, Ano: <ano_publicacao>"`. Crie instâncias dessa classe e use `print()` para exibir as informações.
    1. Crie uma classe `Produto` com os atributos `nome` e `preco`. Implemente o método `__str__` para que retorne uma string que diga: `"Produto: <nome>, Preço: R$ <preco>"`. Crie pelo menos 3 instâncias dessa classe e exiba as informações de cada produto usando `print()`.
    1. Faça uma classe `Pessoa` com os atributos `nome`, `idade` e `cidade`. No método `__str__`, mostre uma frase que inclua esses atributos em um formato legível. Instancie a classe e use `print()` para mostrar o resultado.
    1. Crie uma classe `Veiculo` com os atributos `marca`, `modelo` e `ano`. Implemente o método `__str__` para que a saída seja algo como: `"Veículo: <marca> <modelo> - Ano: <ano>"`. Crie algumas instâncias e teste a saída.
    1. Crie uma classe `ContaBancaria` que possua os atributos `titular` e `saldo`. Implemente o método `__str__` para exibir: `"Conta de <titular>, Saldo: R$ <saldo>"`. Use instâncias dessa classe com o comando `print()`.
    1. Crie uma classe `Filme` com os atributos `titulo`, `diretor` e `ano_lancamento`. No método `__str__`, mostre uma frase no formato: `"Filme: <titulo> (Dirigido por <diretor> - <ano_lancamento>)"`. Instancie e teste a classe.
    1. Crie uma classe `Jogo` com os atributos `nome`, `plataforma` e `genero`. Implemente o método `__str__` para que a saída seja no formato: `"Jogo: <nome> - Plataforma: <plataforma> - Gênero: <genero>"`. Crie objetos e exiba as informações usando `print()`.
    1. Faça uma classe `Aluno` com os atributos `nome`, `matricula` e `curso`. Implemente o método `__str__` para exibir as informações em uma frase completa. Crie alguns objetos e exiba-os.
    1. Crie uma classe `Cidade` com os atributos `nome`, `estado` e `populacao`. Use o método `__str__` para gerar uma string no formato: `"Cidade: <nome>, Estado: <estado>, População: <populacao>"`. Instancie e teste.
    1. Crie uma classe `Carro` com os atributos `marca`, `modelo` e `cor`. No método `__str__`, exiba a seguinte mensagem: `"Carro: <marca> <modelo> na cor <cor>"`. Crie instâncias e teste com o `print()`.
1. 10 Exercícios para o Método `__repr__`
    1. Crie uma classe `Livro` com os atributos `titulo`, `autor` e `ano_publicacao`. Implemente o método `__repr__` para retornar: `"Livro(titulo='<titulo>', autor='<autor>', ano_publicacao=<ano_publicacao>)"`. Crie instâncias e chame `repr()` para testar.
    1. Faça uma classe `Produto` com os atributos `nome` e `preco`. Implemente o método `__repr__` para retornar uma string que reproduza a criação do objeto, como: `"Produto(nome='<nome>', preco=<preco>)"`. Teste no terminal do Python.
    1. Crie uma classe `Pessoa` com os atributos `nome`, `idade` e `cidade`. Implemente o método `__repr__` de forma que ele retorne uma string no formato: `"Pessoa(nome='<nome>', idade=<idade>, cidade='<cidade>')"`. Teste com o comando `repr()`.
    1. Crie uma classe `ContaBancaria` com os atributos `titular` e `saldo`. No método `__repr__`, retorne: `"ContaBancaria(titular='<titular>', saldo=<saldo>)"`. Instancie e teste no terminal chamando `repr()`.
    1. Crie uma classe `Carro` com os atributos `marca`, `modelo` e `ano`. Implemente o método `__repr__` de forma que retorne a seguinte string: `"Carro(marca='<marca>', modelo='<modelo>', ano=<ano>)"`. Use `repr()` para verificar.
    1. Crie uma classe `Filme` com os atributos `titulo`, `diretor` e `ano_lancamento`. No método `__repr__`, retorne algo como: `"Filme(titulo='<titulo>', diretor='<diretor>', ano_lancamento=<ano_lancamento>)"`. Teste no terminal chamando `repr()`.
    1. Faça uma classe `Aluno` com os atributos `nome`, `matricula` e `curso`. No método `__repr__`, exiba algo no formato: `"Aluno(nome='<nome>', matricula='<matricula>', curso='<curso>')"`. Instancie objetos e teste com `repr()`.
    1. Crie uma classe `Jogo` com os atributos `nome`, `plataforma` e `genero`. No método `__repr__`, retorne algo como: `"Jogo(nome='<nome>', plataforma='<plataforma>', genero='<genero>')"`. Teste o método `repr()`.
    1. Crie uma classe `Cidade` com os atributos `nome`, `estado` e `populacao`. Implemente o método `__repr__` para retornar: `"Cidade(nome='<nome>', estado='<estado>', populacao=<populacao>)"`. Teste o método.
    1. Crie uma classe `Empresa` com os atributos `nome`, `fundacao` e `localizacao`. No método `__repr__`, retorne: `"Empresa(nome='<nome>', fundacao=<fundacao>, localizacao='<localizacao>')"`. Crie instâncias e chame `repr()`.

</details>

## métodos mágicos de operadores aritméticos

Os métodos mágicos dos operadores aritméticos permitem que se defina como os objetos de uma classe personalizada devem se comportar quando são envolvidos em operações matemáticas, como adição, subtração, multiplicação, etc. Esses métodos são chamados **sobrecarga de operadores** (operator overloading), já que permitem redefinir o comportamento de operadores padrão (como `+`, `-`, `*`, etc.) para tipos definidos pelo usuário.

Uma lista completa deles pode ser encontrada [aqui](https://docs.python.org/3/reference/datamodel.html#emulating-numeric-types).

### lista de alguns métodos mágicos aritméticos

- `__add__(self, other)` : adição (`+`)
- `__sub__(self, other)` : subtração (`-`)
- `__mul__(self, other)` : multiplicação (`*`)
- `__truediv__(self, other)` : divisão (`/`)
- `__floordiv__(self, other)` : divisão inteira (`//`)
- `__mod__(self, other)` : módulo (resto da divisão) (`%`)
- `__pow__(self, other)` : exponenciação (`**`)

Observe que todos esses métodos recebem um segundo argumento chamado `other`. Na maioria dos casos, esse argumento deve ser do mesmo tipo que `self` ou um tipo compatível. Se esse não for o caso, pode-se levantar um erro.

### `__add__()`

O método `__add__(self, other)` define o comportamento para o operador `+`. Ele é chamado quando se tenta adicionar dois objetos.

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __add__(self, outro):
        print('__add__ chamado')
        return Numero(self.valor + outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

# criando dois objetos
num1 = Numero(10)
num2 = Numero(20)

# usando o operador de adição
soma = num1 + num2
# __add__ chamado
print(soma)
# saída :
# Numero(30)
```

Neste exemplo, `__add__` define o comportamento do operador `+` para a classe `Numero`, retornando um novo objeto `Numero` com o valor somado.

### `__sub__()`

O método `__sub__(self, other)` define o comportamento para o operador de subtração (`-`).

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __sub__(self, outro):
        print('__sub__ chamado')
        return Numero(self.valor - outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(30)
num2 = Numero(10)

subtracao = num1 - num2
# __sub__ chamado
print(subtracao)
# saída :
# Numero(20)
```

### `__mul__()`

O método `__mul__(self, other)` define o comportamento para a multiplicação (`*`).

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __mul__(self, outro):
        print('__mul__ chamado')
        return Numero(self.valor * outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(5)
num2 = Numero(3)

multiplicacao = num1 * num2
# __mul__ chamado
print(multiplicacao)
# saída :
# Numero(15)
```

### `__truediv__()`

O método `__truediv__(self, other)` define o comportamento para a divisão (`/`).

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __truediv__(self, outro):
        print('__truediv__ chamado')
        return Numero(self.valor / outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(10)
num2 = Numero(2)

divisao = num1 / num2
# __truediv__ chamado
print(divisao)
# saída :
# Numero(5.0)
```

### `__floordiv__()`

O método `__floordiv(self, other)` define o comportamento para a divisão inteira (`//`).

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __floordiv__(self, outro):
        print('__floordiv__ chamado')
        return Numero(self.valor // outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(10)
num2 = Numero(3)

divisao_inteira = num1 // num2
# __floordiv__ chamado
print(divisao_inteira)
# saída :
# Numero(3.0)
```

### `__mod__()`

O método `__mod__(self, other)` define o comportamento para o operador de módulo (`%`), que retorna o resto da divisão.

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __mod__(self, outro):
        print('__mod__ chamado')
        return Numero(self.valor % outro.valor)

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(10)
num2 = Numero(3)

modulo = num1 % num2
# __mod__ chamado
print(modulo)  # saída : Numero(1)
# saída :
# Numero(1)
```

### `__pow__()`

O método `__pow__(self, other[, modulo])` define o comportamento para a exponenciação (`**`).

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __pow__(self, outro, modulo=None):
        print('__pow__ chamado')
        if modulo is None:
            return Numero(self.valor ** outro.valor)
        return Numero(pow(self.valor, outro, modulo))

    def __repr__(self):
        return f"Numero({self.valor})"

num1 = Numero(2)
num2 = Numero(3)

exponenciacao = num1 ** num2
# __pow__ chamado
print(exponenciacao)
# saída :
# Numero(8)
```

### operadores reflexivos

Os operadores reflexivos são usados quando o objeto à esquerda da operação não pode realizar a operação e, portanto, o Python tenta chamar a operação inversa no objeto à direita.

- **`__radd__(self, other)`** : reflexivo da adição
- **`__rsub__(self, other)`** : reflexivo da subtração
- **`__rmul__(self, other)`** : reflexivo da multiplicação
- **`__rtruediv__(self, other)`** : reflexivo da divisão
- **`__rfloordiv__(self, other)`** : reflexivo da divisão inteira
- **`__rmod__(self, other)`** : reflexivo do módulo (resto da divisão)
- **`__rpow__(self, other[, modulo])`** : reflexivo da exponenciação

Esses métodos são úteis quando se deseja permitir que operações entre objetos de tipos diferentes sejam realizadas corretamente.

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __add__(self, outro):
        print('__add__ chamado')
        return Numero(self.valor + outro.valor)

    def __radd__(self, outro):
        print("__radd__ chamado")
        return Numero(self.valor + outro)

    def __repr__(self):
        return f"Numero({self.valor})"

# criando dois objetos
num1 = Numero(10)
num2 = Numero(20)

# usando o operador de adição
soma = num1 + num2
# __add__ chamado
print(soma)
# saída :
# Numero(30)

# usando um objeto do tipo inteiro
soma = 2 + num1
# __radd__ chamado
print(soma)
# saída :
# Numero(12)
```

---

### operadores in-place

Os **operadores in-place** são utilizados para modificar o objeto à esquerda em vez de criar um novo. Eles correspondem aos operadores como `+=`, `-=`, `*=`, etc.

- `__iadd__(self, other)` para `self += other`
- `__isub__(self, other)` para `self -= other`
- `__imul__(self, other)` para `self *= other`
- `__itruediv__(self, other)` para `self /= other`
- `__ifloordiv__(self, other)` para `self //= other`
- `__imod__(self, other)` para `self %= other`
- `__ipow__(self, other[, modulo])` para `self **= other`

**Exemplo**

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __add__(self, outro):
        print('__add__ chamado')
        return Numero(self.valor + outro.valor)

    def __iadd__(self, outro):
        print('__iadd__ chamado')
        self.valor += outro
        return self

    def __repr__(self):
        return f"Numero({self.valor})"

num = Numero(10)
num += 5  # modifica o próprio objeto em vez de criar um novo
# __iadd__ chamado
print(num)  # saída : Numero(15)
```

Neste exemplo, o operador `+=` modifica o valor de `num` diretamente, graças à implementação do método `__iadd__`. Sem ele, a operação `+=` criaria um novo objeto ao invés de modificar o existente.

### exemplo completo

Abaixo há um exemplo completo da aplicação dos três métodos mágicos da soma. O mesmo raciocínio pode ser feito para os demais operadores.

```python
class Numero:
    def __init__(self, valor):
        self.valor = valor

    def __add__(self, outro):
        print('__add__ chamado')
        if isinstance(outro, Numero):
            return Numero(self.valor + outro.valor)
        elif isinstance(outro, int | float):
            return Numero(self.valor + outro)
        else:
            raise TypeError("operação de tipo não suportado para +")

    def __radd__(self, outro):
        print("__radd__ chamado")
        return self.__add__(outro)

    def __iadd__(self, outro):
        print('__iadd__ chamado')
        self.valor += outro
        return self

    def __repr__(self):
        return f"Numero({self.valor})"

# criando dois objetos
num1 = Numero(10)
num2 = Numero(20)

soma = num1 + num2
# __add__ chamado
print(soma, end='\n\n')  # saída : Numero(30)

soma = 2 + num1
# __radd__ chamado
# __add__ chamado
print(soma, end='\n\n')  # saída : Numero(12)

num1 += 5
# __iadd__ chamado
print(num1, end='\n\n')  # saída : Numero(15)

num1 += num2
# __iadd__ chamado
# __radd__ chamado
# __add__ chamado
print(num1, end='\n\n')  # saída : Numero(30)
```

- Repare nas 3 chamadas quando é feita a operação `num1 += num2`.

## exercícios métodos mágicos operadores aritméticos

<details>
<summary>Lista de Exercícios</summary>

1. Exercícios para `__add__`, `__radd__`, e `__iadd__`
    1. Crie uma classe `Numero` que implemente o método mágico `__add__` para somar dois objetos dessa classe.
    1. Modifique a classe `Numero` para que também possa somar um número inteiro ou float a um objeto `Numero` utilizando `__add__`.
    1. Implemente o método mágico `__radd__` na classe `Numero` para permitir que a adição funcione quando um número é somado a um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a soma utilizando o operador `+`. Observe a saída.
    1. Teste a classe `Numero` somando um número inteiro a um objeto `Numero`. Verifique se `__radd__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__iadd__` e permita que o operador `+=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `+=` para adicionar um valor a ele. Verifique se o objeto foi modificado corretamente.
    1. Tente somar dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `+=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__add__`, `__radd__` e `__iadd__` para somar frações.
    1. Teste a classe `Fracao` somando frações e utilizando o operador `+=` para modificar o objeto original.
1. Exercícios para `__sub__`, `__rsub__`, e `__isub__`
    1. Crie uma classe `Numero` que implemente o método mágico `__sub__` para subtrair dois objetos da classe.
    1. Modifique a classe `Numero` para que também possa subtrair um número inteiro ou float de um objeto `Numero` utilizando `__sub__`.
    1. Implemente o método mágico `__rsub__` na classe `Numero` para permitir que a subtração funcione quando um número é subtraído de um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a subtração utilizando o operador `-`. Observe a saída.
    1. Teste a classe `Numero` subtraindo um número inteiro de um objeto `Numero`. Verifique se `__rsub__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__isub__` e permita que o operador `-=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `-=` para subtrair um valor dele. Verifique se o objeto foi modificado corretamente.
    1. Tente subtrair dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `-=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__sub__`, `__rsub__` e `__isub__` para subtrair frações.
    1. Teste a classe `Fracao` subtraindo frações e utilizando o operador `-=` para modificar o objeto original.
1. Exercícios para `__mul__`, `__rmul__`, e `__imul__`
    1. Crie uma classe `Numero` que implemente o método mágico `__mul__` para multiplicar dois objetos dessa classe.
    1. Modifique a classe `Numero` para que também possa multiplicar um número inteiro ou float a um objeto `Numero` utilizando `__mul__`.
    1. Implemente o método mágico `__rmul__` na classe `Numero` para permitir que a multiplicação funcione quando um número é multiplicado por um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a multiplicação utilizando o operador `*`. Observe a saída.
    1. Teste a classe `Numero` multiplicando um número inteiro a um objeto `Numero`. Verifique se `__rmul__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__imul__` e permita que o operador `*=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `*=` para multiplicá-lo por um valor. Verifique se o objeto foi modificado corretamente.
    1. Tente multiplicar dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `*=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__mul__`, `__rmul__` e `__imul__` para multiplicar frações.
    1. Teste a classe `Fracao` multiplicando frações e utilizando o operador `*=` para modificar o objeto original.
1. Exercícios para `__truediv__`, `__rtruediv__`, e `__itruediv__`
    1. Crie uma classe `Numero` que implemente o método mágico `__truediv__` para dividir dois objetos dessa classe.
    1. Modifique a classe `Numero` para que também possa dividir um número inteiro ou float por um objeto `Numero` utilizando `__truediv__`.
    1. Implemente o método mágico `__rtruediv__` na classe `Numero` para permitir que a divisão funcione quando um número é dividido por um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a divisão utilizando o operador `/`. Observe a saída.
    1. Teste a classe `Numero` dividindo um número inteiro por um objeto `Numero`. Verifique se `__rtruediv__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__itruediv__` e permita que o operador `/=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `/=` para dividi-lo por um valor. Verifique se o objeto foi modificado corretamente.
    1. Tente dividir dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `/=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__truediv__`, `__rtruediv__` e `__itruediv__` para dividir frações.
    1. Teste a classe `Fracao` dividindo frações e utilizando o operador `/=` para modificar o objeto original.
1. Exercícios para `__floordiv__`, `__rfloordiv__`, e `__ifloordiv__`
    1. Crie uma classe `Numero` que implemente o método mágico `__floordiv__` para realizar divisão inteira entre dois objetos dessa classe.
    1. Modifique a classe `Numero` para que também possa realizar divisão inteira entre um número inteiro ou float e um objeto `Numero` utilizando `__floordiv__`.
    1. Implemente o método mágico `__rfloordiv__` na classe `Numero` para permitir que a divisão inteira funcione quando um número inteiro é dividido por um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a divisão inteira utilizando o operador `//`. Observe a saída.
    1. Teste a classe `Numero` dividindo um número inteiro por um objeto `Numero` usando divisão inteira. Verifique se `__rfloordiv__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__ifloordiv__` e permita que o operador `//=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `//=` para realizar divisão inteira nele. Verifique se o objeto foi modificado corretamente.
    1. Tente realizar a divisão inteira entre dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `//=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__floordiv__`, `__rfloordiv__` e `__ifloordiv__` para realizar divisão inteira entre frações.
    1. Teste a classe `Fracao` realizando divisões inteiras entre frações e utilizando o operador `//=` para modificar o objeto original.
1. Exercícios para `__mod__`, `__rmod__`, e `__imod__`
    1. Crie uma classe `Numero` que implemente o método mágico `__mod__` para calcular o resto da divisão (módulo) entre dois objetos dessa classe.
    1. Modifique a classe `Numero` para que também possa calcular o módulo entre um número inteiro ou float e um objeto `Numero` utilizando `__mod__`.
    1. Implemente o método mágico `__rmod__` na classe `Numero` para permitir que o cálculo do módulo funcione quando um número é dividido por um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a operação de módulo utilizando o operador `%`. Observe a saída.
    1. Teste a classe `Numero` calculando o módulo de um número inteiro e um objeto `Numero`. Verifique se `__rmod__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__imod__` e permita que o operador `%=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `%=` para calcular o módulo dele por outro valor. Verifique se o objeto foi modificado corretamente.
    1. Tente calcular o módulo entre dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `%=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__mod__`, `__rmod__` e `__imod__` para calcular o módulo entre frações.
    1. Teste a classe `Fracao` calculando o módulo entre frações e utilizando o operador `%=` para modificar o objeto original.
1. Exercícios para `__pow__`, `__rpow__`, e `__ipow__`
    1. Crie uma classe `Numero` que implemente o método mágico `__pow__` para elevar um objeto dessa classe à potência de outro objeto da mesma classe.
    1. Modifique a classe `Numero` para que também possa calcular a potência entre um número inteiro ou float e um objeto `Numero` utilizando `__pow__`.
    1. Implemente o método mágico `__rpow__` na classe `Numero` para permitir que a operação de potência funcione quando um número é elevado à potência de um objeto `Numero`.
    1. Crie dois objetos da classe `Numero` e realize a operação de potência utilizando o operador `**`. Observe a saída.
    1. Teste a classe `Numero` calculando a potência de um número inteiro elevado a um objeto `Numero`. Verifique se `__rpow__` foi chamado corretamente.
    1. Modifique a classe `Numero` para implementar o método `__ipow__` e permita que o operador `**=` modifique o objeto original.
    1. Crie um objeto `Numero` e utilize o operador `**=` para elevar o objeto à potência de outro valor. Verifique se o objeto foi modificado corretamente.
    1. Tente calcular a potência entre dois objetos `Numero` e atribuí-los diretamente a um deles usando o operador `**=`. Verifique o resultado.
    1. Crie uma classe `Fracao` que implemente os métodos `__pow__`, `__rpow__` e `__ipow__` para calcular a potência entre frações.
    1. Teste a classe `Fracao` calculando a potência de frações e utilizando o operador `**=` para modificar o objeto original.

</details>

## herança

**Herança** é um dos principais conceitos da programação orientada a objetos (POO). Ela permite que uma classe herde atributos e métodos de outra classe, promovendo **reutilização de código** e **organização** do sistema. No contexto de Python, a herança ocorre quando uma nova classe (chamada de **classe derivada** ou **subclasse**) é criada a partir de uma classe existente (chamada de **classe base** ou **superclasse**), herdando os seus atributos e métodos.

A principal vantagem da herança é que ela evita a duplicação de código. Ao invés de reescrever métodos ou atributos comuns entre várias classes, podemos defini-los uma vez na classe base e permitir que as subclasses os utilizem diretamente.

### como funciona

Quando uma classe herda de outra, ela recebe todos os atributos e métodos da classe base, e pode utilizar ou invocar esses recursos como se fossem seus próprios. Isso facilita a criação de subclasses mais especializadas que compartilham um comportamento comum.

#### sintaxe básica

Em Python, para definir uma classe que herda de outra, é usada a seguinte sintaxe:

```python
class ClasseBase:
    # atributos e métodos da classe base
    def __init__(self, atributo_base):
        self.atributo_base = atributo_base

    def metodo_base(self):
        return f"Atributo base: {self.atributo_base}"

# Subclasse que herda de ClasseBase
class Subclasse(ClasseBase):
    # atributos e métodos da subclasse
    pass
```

Aqui, `Subclasse` herda de `ClasseBase`. A palavra-chave `pass` indica que a subclasse não tem definições adicionais. Mas, mesmo que não adicionemos novos métodos ou atributos na subclasse, ela ainda terá acesso ao que foi definido na `ClasseBase`.

#### exemplo

Vamos agora ver um exemplo mais concreto:

```python
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def fazer_som(self):
        return f"{self.nome} está fazendo um som."

class Cachorro(Animal):
    pass

# criando uma instância de Cachorro
meu_cachorro = Cachorro("Rex")
print(meu_cachorro.fazer_som())  # saída : Rex está fazendo um som.
```

Neste exemplo:
- A classe `Animal` é a **superclasse**, e a classe `Cachorro` é a **subclasse**.
- A subclasse `Cachorro` herda o comportamento (atributo `nome` e método `fazer_som()`) da classe `Animal`.
- Quando criamos um objeto da classe `Cachorro` (`meu_cachorro`), ele já pode usar o método `fazer_som()` da classe base `Animal`.

Isso ocorre porque o Python, ao tentar acessar um método ou atributo na subclasse, primeiro verifica se o método ou atributo existe diretamente na subclasse. Se não encontrar, ele sobe na hierarquia de classes e busca na superclasse.

### inicialização com o método `__init__`

Uma das características mais comuns na herança é o uso do método especial `__init__()` (construtor). Quando uma subclasse herda de uma superclasse, o método `__init__()` da superclasse não é chamado automaticamente. É preciso invocá-lo manualmente para garantir que a subclasse seja corretamente inicializada.

#### exemplo

```python
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def fazer_som(self):
        return f"{self.nome} está fazendo um som."

class Cachorro(Animal):
    def __init__(self, nome, raca):
        # chamando o __init__ da classe base
        super().__init__(nome)
        self.raca = raca

    def descricao(self):
        return f"{self.nome} é um {self.raca}"

# criando uma instância de Cachorro
meu_cachorro = Cachorro("Rex", "Golden Retriever")
print(meu_cachorro.descricao())  # saída : Rex é um Golden Retriever
print(meu_cachorro.fazer_som())  # saída : Rex está fazendo um som.
```

Aqui, temos o seguinte fluxo:
- a classe `Cachorro` tem um método `__init__()` próprio, que além de receber o nome, também aceita a raça do cachorro;
- dentro do `__init__()` da classe `Cachorro`, usamos `super().__init__(nome)` para chamar o construtor da classe `Animal` e inicializar o atributo `nome`;
- a subclasse `Cachorro` ainda tem acesso ao método `fazer_som()` da classe `Animal` e pode usá-lo normalmente;

### atributos herdados

**Atributos** são variáveis associadas a objetos de uma classe. Quando uma subclasse herda de uma superclasse, ela herda todos os atributos definidos na superclasse. Isso inclui :
- atributos de instância (definidos dentro de métodos, normalmente dentro do `__init__()`);
- atributos de classe (definidos diretamente no corpo da classe, fora de métodos);

#### como funciona?

1. **Atributos de Instância:**

    Quando uma subclasse herda de uma superclasse, os atributos de instância da superclasse também fazem parte das instâncias da subclasse, desde que o construtor da superclasse (`__init__()`) seja chamado adequadamente.

    Exemplo:
    ```python
    class Animal:
        def __init__(self, nome):
            self.nome = nome  # atributo de instância

    class Cachorro(Animal):
        pass

    rex = Cachorro("Rex")
    print(rex.nome)  # saída : Rex
    ```

    - `self.nome` é um **atributo de instância** definido na classe `Animal`;
    - quando um objeto da classe `Cachorro` é criado, ele herda o atributo `nome` da classe `Animal` porque a subclasse `Cachorro` não sobrescreve o `__init__()` da superclasse;

2. **Atributos de Classe:**

    Atributos de classe são compartilhados por todas as instâncias de uma classe, incluindo suas subclasses. Eles são definidos diretamente no corpo da classe e não no construtor.

    Exemplo:
    ```python
    class Animal:
        especie = "Mamífero"  # atributo de classe

    class Cachorro(Animal):
        pass

    rex = Cachorro("Rex")
    print(rex.especie)  # saída : Mamífero
    ```

    - `especie` é um **atributo de classe** definido na superclasse `Animal`;
    - a subclasse `Cachorro` herda esse atributo, portanto qualquer instância da classe `Cachorro` pode acessar `especie`;

#### importante

- **Atributos de Instância** : são definidos para cada instância individualmente. Para que a subclasse herde corretamente os atributos de instância, normalmente é necessário chamar o método `__init__()` da superclasse usando `super()`;
- **Atributos de Classe** : são compartilhados por todas as instâncias da classe e suas subclasses, a menos que sejam sobrescritos;

### métodos herdados

**Métodos** são funções definidas dentro de uma classe, que manipulam os atributos de instância ou realizam outras operações. Quando uma subclasse herda de uma superclasse, ela também herda todos os métodos da superclasse. Isso significa que a subclasse pode chamar diretamente os métodos definidos na superclasse, sem precisar reescrevê-los.

#### como funciona?

Quando um método é chamado em uma instância de uma subclasse, o Python segue a **ordem de resolução de métodos (MRO)**, que significa que:
1. o Python verifica primeiro se o método existe na subclasse;
1. se não encontrar, ele sobe para a superclasse e verifica lá;

Se o método estiver definido na superclasse, a subclasse poderá utilizá-lo automaticamente, como se fosse parte dela.

```python
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def fazer_som(self):
        return f"{self.nome} está fazendo um som."

class Cachorro(Animal):
    pass

# criando um objeto da subclasse Cachorro
rex = Cachorro("Rex")

# chamando o método herdado da superclasse
print(rex.fazer_som())  # saída : Rex está fazendo um som.
```

Neste exemplo:
- a subclasse `Cachorro` herda o método `fazer_som()` da classe `Animal`;
- quando uma instância de `Cachorro` é criada, o objeto `rex` pode chamar o método `fazer_som()` diretamente, sem que ele tenha sido explicitamente definido na classe `Cachorro`;

#### modificações em métodos herdados

Embora a subclasse herde métodos diretamente da superclasse, ela pode:
1. **Usar os métodos da superclasse sem modificações** : como nos exemplos acima;
1. **Sobrescrever os métodos herdados** : a subclasse pode sobrescrever os métodos herdados;
1. **Adicionar novos métodos** : a subclasse pode definir seus próprios métodos, além dos herdados;

    Exemplo:
    ```python
    class Animal:
        def fazer_som(self):
            return "Som genérico de animal"

    class Cachorro(Animal):
        def latir(self):
            return f"{self.nome} está latindo!"

        def fazer_som(self):
            return "Som específico do Cachorro"

    rex = Cachorro("Rex")
    print(rex.fazer_som())  # método herdado, mas sobrescrito
    print(rex.latir())      # método novo da subclasse
    ```

    Aqui, `Cachorro` herda e sobrescreve o método `fazer_som()` da classe `Animal` e, além disso, define um novo método `latir()`.

### sobrecarga de métodos

Em Python, é possível sobrescrever (ou seja, redefinir) métodos de uma superclasse na subclasse. Quando isso acontece, o método da subclasse é chamado, em vez do método da superclasse.

No exemplo anterior, a classe `Cachorro` sobrescreveu o método `emitir_som` da classe base `Animal`. Se quiser ainda assim acessar o método da superclasse dentro da subclasse, pode-se usar `super()`.

```python
class Cachorro(Animal):
    def emitir_som(self):
        # chamando o método da classe base
        super().emitir_som()
        print(f'{self.nome} também está latindo.')
```

### como o python procura atributos e métodos?

Quando um método ou atributo de uma instância é acessado, o Python segue a seguinte ordem de busca:

1. **Subclasse :** primeiro, o Python verifica se o método ou atributo existe na subclasse;
1. **Superclasse :** se não for encontrado na subclasse, ele sobe para a superclasse e verifica lá;
1. **Mais acima (se houver) :** se houver classes acima na hierarquia, ele continua a busca até encontrar o que está sendo procurado ou até esgotar todas as opções;

Essa cadeia de busca é chamada de **MRO** (Method Resolution Order), que basicamente é a ordem de busca que o Python segue para encontrar métodos e atributos.

#### exemplo de MRO

```python
class A:
    def metodo(self):
        print("Método de A")

class B(A):
    pass

class C(B):
    pass

objeto = C()
objeto.metodo()  # saída : Método de A
```

Neste exemplo, o objeto da classe `C` está chamando `metodo()`. Como a classe `C` e a classe `B` não possuem esse método, o Python vai até a classe `A` e o encontra lá.

É possível verificar a ordem de resolução de métodos usando o método `mro()` ou a função `help()`.

```python
print(objeto.mro())
```

Isso mostra a sequência que o Python segue para encontrar o método ou atributo solicitado.

## exercícios herança

<details>
<summary>Lista de Exercícios</summary>

1. Herança Simples
    1. Crie uma classe `Veiculo` com um atributo `marca`. Crie uma subclasse `Carro` que herde de `Veiculo`. Instancie um objeto de `Carro` e defina a marca.
    1. Implemente uma classe `Animal` com um método `fazer_som()` que imprima "Som genérico". Crie uma subclasse `Gato` que herde de `Animal` e teste o método herdado.
    1. Crie uma classe `Pessoa` com um atributo `nome`. Crie uma subclasse `Estudante` que herde de `Pessoa` e instancie um objeto de `Estudante`. Defina o nome e imprima-o.
    1. Crie uma classe `Eletronico` com um método `ligar()`. Crie uma subclasse `Computador` que herde de `Eletronico` e utilize o método `ligar()`.
    1. Crie uma classe `InstrumentoMusical` com um método `tocar()`. Crie uma subclasse `Violao` que herde de `InstrumentoMusical` e utilize o método herdado.
    1. Implemente uma classe `Funcionario` com um método `trabalhar()` que imprime "Trabalhando". Crie uma subclasse `Programador` que herde de `Funcionario` e utilize o método `trabalhar()`.
    1. Desenvolva uma classe `Produto` com um método `informar_preco()` que imprime "Preço não definido". Crie uma subclasse `Eletronico` e teste o método herdado.
    1. Crie uma classe `Bicicleta` com um método `pedalar()`. Crie uma subclasse `MountainBike` que herde de `Bicicleta` e utilize o método `pedalar()`.
    1. Crie uma classe `Telefone` com um método `ligar()`. Crie uma subclasse `Smartphone` e utilize o método herdado.
    1. Desenvolva uma classe `ContaBancaria` com um método `depositar()`. Crie uma subclasse `ContaCorrente` e utilize o método herdado.
1. Herança de Atributos de Instância
    1. Crie uma classe `Pessoa` com os atributos `nome` e `idade`. Crie uma subclasse `Aluno` que herde esses atributos e instancie um objeto de `Aluno`. Defina o nome e a idade e imprima-os.
    1. Implemente uma classe `Veiculo` com os atributos `marca` e `ano`. Crie uma subclasse `Carro` que herde esses atributos. Instancie um objeto de `Carro`, defina os valores dos atributos e imprima-os.
    1. Crie uma classe `Funcionario` com os atributos `nome` e `salario`. Crie uma subclasse `Gerente` que herde esses atributos e instancie um objeto de `Gerente`. Defina o nome e o salário e imprima-os.
    1. Crie uma classe `Animal` com os atributos `nome` e `especie`. Crie uma subclasse `Cachorro` que herde esses atributos. Instancie um objeto de `Cachorro`, defina os atributos e imprima-os.
    1. Implemente uma classe `Produto` com os atributos `nome` e `preco`. Crie uma subclasse `Livro` que herde esses atributos. Instancie um objeto de `Livro`, defina o nome e o preço, e imprima-os.
    1. Desenvolva uma classe `Eletronico` com os atributos `marca` e `modelo`. Crie uma subclasse `Smartphone` que herde esses atributos. Instancie um objeto de `Smartphone`, defina os valores dos atributos e imprima-os.
    1. Crie uma classe `Pessoa` com os atributos `nome` e `endereco`. Crie uma subclasse `Cliente` que herde esses atributos e instancie um objeto de `Cliente`. Defina os valores e imprima-os.
    1. Implemente uma classe `ContaBancaria` com os atributos `titular` e `saldo`. Crie uma subclasse `ContaPoupanca` que herde esses atributos. Instancie um objeto de `ContaPoupanca`, defina o titular e o saldo, e imprima-os.
    1. Desenvolva uma classe `Veiculo` com os atributos `marca` e `velocidade_maxima`. Crie uma subclasse `Moto` que herde esses atributos. Instancie um objeto de `Moto`, defina os atributos e imprima-os.
    1. Crie uma classe `Jogador` com os atributos `nome` e `posicao`. Crie uma subclasse `Atacante` que herde esses atributos e instancie um objeto de `Atacante`. Defina os valores e imprima-os.
1. Herança de Atributos de Classe
    1. Crie uma classe `Pessoa` com um atributo de classe `especie = "Humano"`. Crie uma subclasse `Aluno` que herde esse atributo. Verifique se o atributo é acessível pela subclasse.
    1. Desenvolva uma classe `Veiculo` com um atributo de classe `categoria = "Transporte"`. Crie uma subclasse `Carro` que herde esse atributo e acesse-o através de um objeto da subclasse.
    1. Implemente uma classe `Animal` com um atributo de classe `tipo = "Mamífero"`. Crie uma subclasse `Cachorro` que herde esse atributo e verifique se o objeto da subclasse pode acessá-lo.
    1. Crie uma classe `Produto` com um atributo de classe `tipo = "Mercadoria"`. Crie uma subclasse `Alimento` que herde esse atributo. Instancie um objeto da subclasse e acesse o atributo.
    1. Desenvolva uma classe `Funcionario` com um atributo de classe `empresa = "TechCorp"`. Crie uma subclasse `Engenheiro` que herde esse atributo e acesse-o através de um objeto da subclasse.
    1. Crie uma classe `Eletronico` com um atributo de classe `tipo = "Aparelho"`. Crie uma subclasse `Computador` que herde esse atributo e instancie um objeto para acessá-lo.
    1. Implemente uma classe `ContaBancaria` com um atributo de classe `instituicao = "Banco ABC"`. Crie uma subclasse `ContaCorrente` que herde esse atributo e verifique se o objeto da subclasse pode acessá-lo.
    1. Desenvolva uma classe `Jogador` com um atributo de classe `esporte = "Futebol"`. Crie uma subclasse `Goleiro` que herde esse atributo e acesse-o através de um objeto da subclasse.
    1. Crie uma classe `InstrumentoMusical` com um atributo de classe `categoria = "Cordas"`. Crie uma subclasse `Violao` que herde esse atributo. Instancie um objeto da subclasse e acesse o atributo.
    1. Implemente uma classe `Pessoa` com um atributo de classe `planeta = "Terra"`. Crie uma subclasse `Cientista` que herde esse atributo e acesse-o através de um objeto da subclasse.
1. Herança de Métodos
    1. Crie uma classe `Veiculo` com um método `mover()` que imprime "O veículo está se movendo". Crie uma subclasse `Carro` que herde esse método e teste-o.
    1. Implemente uma classe `Funcionario` com um método `trabalhar()` que imprime "Funcionário está trabalhando". Crie uma subclasse `Gerente` e sobrescreva o método herdado.
    1. Desenvolva uma classe `Produto` com um método `informar_preco()` que imprime "Preço não definido". Crie uma subclasse `Alimento` e utilize o método herdado.
    1. Crie uma classe `Pessoa` com um método `falar()` que imprime "Olá, eu sou uma pessoa". Crie uma subclasse `Aluno` e sobrescreva o método herdado.
    1. Implemente uma classe `Animal` com um método `comer()` que imprime "O animal está comendo". Crie uma subclasse `Leao` e utilize o método herdado.
    1. Desenvolva uma classe `InstrumentoMusical` com um método `tocar()` que imprime "Tocando instrumento". Crie uma subclasse `Guitarra` e sobrescreva o método herdado.
    1. Crie uma classe `Veiculo` com um método `parar()` que imprime "O veículo está parando". Crie uma subclasse `Moto` e utilize o método herdado.
    1. Implemente uma classe `Funcionario` com um método `descansar()` que imprime "Funcionário está descansando". Crie uma subclasse `Programador` e sobrescreva o método herdado.
    1. Desenvolva uma classe `Eletronico` com um método `desligar()` que imprime "Aparelho desligado". Crie uma subclasse `Tablet` e utilize o método herdado.
    1. Crie uma classe `Jogador` com um método `correr()` que imprime "Jogador está correndo". Crie uma subclasse `Atacante` e sobrescreva o método herdado.

</details>

## métodos mágicos de operadores de comparação

Também é possível encontrar que métodos especiais estão por trás dos operadores de comparação. Por exemplo, quando se executa algo como `5 < 2`, Python chama o método mágico `.__lt__()`.

Veja a tabela abaixo desses métodos :

| Operador | Método de Suporte |
|---|---|
| `<` | `.__lt__(self, other)` |
| `<=` | `.__le__(self, other)` |
| `==` | `.__eq__(self, other)` |
| `!=` | `.__ne__(self, other)` |
| `>=` | `.__ge__(self, other)` |
| `>` | `.__gt__(self, other)` |

Veja abaixo a classe `Retangulo` que aplica esses métodos mágicos para comparar a área do objeto.

```python
class retangulo:
    def __init__(self, altura, largura):
        self.altura = altura
        self.largura = largura

    def area(self):
        return self.altura * self.largura

    def __eq__(self, other):
        return self.area() == other.area()

    def __lt__(self, other):
        return self.area() < other.area()

    def __gt__(self, other):
        return self.area() > other.area()
```

A classe possui um método `.area()` que calcula a área do retângulo usando sua altura e largura. Em seguida, há três métodos mágicos necessários para suportar os operadores de comparação pretendidos. Observe que todos eles usam a área do retângulo para determinar o resultado final.

Veja como fica aplicado na prática :

```python
quadra_basquete = Retangulo(15, 28)
quadra_futebol = Retangulo(75, 110)

print(quadra_basquete < quadra_futebol)
# saída : True
print(quadra_basquete > quadra_futebol)
# saída : False
print(quadra_basquete == quadra_futebol)
# saída : False
```

## exercícios métodos mágicos de operadores de comparação

<details>
<summary>Lista de Exercícios</summary>

1. Exercícios para `__lt__(self, other)` (menor que)
    1. **Crie uma classe `Produto`** com um atributo `preco`. Implemente o método `__lt__` para que possa comparar dois produtos com base no preço.
    1. **Implemente a classe `Data`** com atributos `dia`, `mes` e `ano`. Use o método `__lt__` para comparar duas datas e determinar se uma data é anterior à outra.
    1. **Crie uma classe `Pessoa`** com um atributo `idade`. Implemente `__lt__` para que você possa verificar se uma pessoa é mais jovem que outra.
    1. **Desenvolva uma classe `Quadrado`** que tem um atributo `lado`. Implemente `__lt__` para que você possa comparar dois quadrados com base na área.
    1. **Crie uma classe `Nota`** que representa uma nota escolar com um atributo `valor`. Use `__lt__` para determinar se uma nota é menor que outra.
1. Exercícios para `__le__(self, other)` (menor ou igual a)
    1. **Use a classe `Produto`** do exercício anterior e adicione o método `__le__` para permitir a comparação de preços, incluindo igualdade.
    1. **Modifique a classe `Data`** para implementar `__le__`, permitindo que você compare se uma data é anterior ou igual a outra.
    1. **Adicione o método `__le__` à classe `Pessoa`** para que você possa verificar se uma pessoa é mais jovem ou da mesma idade que outra.
    1. **Use a classe `Quadrado`** do exercício anterior e implemente `__le__` para comparar a área de dois quadrados, permitindo igualdade.
    1. **Crie uma classe `Nota`** com o método `__le__` que permite verificar se uma nota é menor ou igual a outra.
1. Exercícios para `__eq__(self, other)` (igual a)
    1. **Crie uma classe `Produto`** que tenha um atributo `codigo`. Implemente `__eq__` para comparar produtos com base no código.
    1. **Desenvolva a classe `Data`** para incluir o método `__eq__`, permitindo verificar se duas datas são iguais.
    1. **Implemente `__eq__` na classe `Pessoa`** para comparar duas pessoas com base no nome e idade.
    1. **Adicione o método `__eq__` à classe `Quadrado`** para que você possa verificar se dois quadrados têm a mesma área.
    1. **Crie uma classe `Nota`** com um atributo `disciplina` e implemente `__eq__` para comparar notas de diferentes disciplinas.
1. Exercícios para `__ne__(self, other)` (diferente de)
    1. **Utilize a classe `Produto`** do primeiro exercício e implemente `__ne__` para verificar se dois produtos são diferentes com base no preço.
    1. **Modifique a classe `Data`** para incluir o método `__ne__`, permitindo que você compare se duas datas são diferentes.
    1. **Adicione o método `__ne__` à classe `Pessoa`** para determinar se duas pessoas são diferentes com base na idade.
    1. **Use a classe `Quadrado`** e implemente `__ne__` para verificar se dois quadrados têm áreas diferentes.
    1. **Crie uma classe `Nota`** com o método `__ne__` para comparar notas e verificar se são diferentes.
1. Exercícios para `__ge__(self, other)` (maior ou igual a)
    1. **Implemente o método `__ge__` na classe `Produto`** para comparar produtos com base no preço, permitindo verificar se um produto é mais caro ou igual a outro.
    1. **Adicione `__ge__` à classe `Data`** para que você possa comparar se uma data é posterior ou igual a outra.
    1. **Modifique a classe `Pessoa`** para implementar `__ge__`, permitindo que você verifique se uma pessoa é mais velha ou da mesma idade que outra.
    1. **Use a classe `Quadrado`** do exercício anterior e implemente `__ge__` para comparar áreas, permitindo verificar se uma área é maior ou igual a outra.
    1. **Crie uma classe `Nota`** e adicione `__ge__` para permitir verificar se uma nota é maior ou igual a outra.
1. Exercícios para `__gt__(self, other)` (maior que)
    1. **Crie uma classe `Produto`** com um atributo `preco` e implemente `__gt__` para comparar produtos com base no preço.
    1. **Implemente a classe `Data`** e use `__gt__` para determinar se uma data é posterior a outra.
    1. **Adicione `__gt__` à classe `Pessoa`** para que você possa verificar se uma pessoa é mais velha que outra.
    1. **Utilize a classe `Quadrado`** e implemente `__gt__` para comparar áreas e verificar se um quadrado é maior que o outro.
    1. **Crie uma classe `Nota`** com o método `__gt__` que permite verificar se uma nota é maior que outra.

</details>

## métodos estáticos

Métodos estáticos são uma forma de definir funções dentro de uma classe que não requerem uma referência a uma instância da classe para serem chamadas. Eles são marcados com o decorador `@staticmethod` e não têm acesso direto ao estado da instância ou à classe.

- **definição** : um método estático é um método que pertence à classe, não a uma instância da classe; isso significa que ela pode ser chamada sem criar um objeto da classe;
- **acesso** : métodos estáticos não têm acesso a `self` (a instância da classe) ou `cls` (a própria classe); eles não podem modificar o estado da instância ou da classe;

### quando usar

Os métodos estáticos são úteis quando:

1. **Encapsulamento de Funções Relacionadas** : se deseja agrupar funções que fazem parte da lógica da classe, mas que não precisam acessar os dados da instância ou da classe;
1. **Organização** : eles ajudam a organizar o código de maneira mais limpa e clara, separando a lógica que não depende do estado da instância;

### como definir

Veja a sintaxe para definir um método estático :

```python
class MinhaClasse:
    @staticmethod
    def meu_metodo_estatico(param):
        return f"Você passou {param}."
```

Veja um exemplo prático :

```python
class Calculadora:

    @staticmethod
    def somar(a, b):
        return a + b

    @staticmethod
    def subtrair(a, b):
        return a - b

    @staticmethod
    def multiplicar(a, b):
        return a * b

    @staticmethod
    def dividir(a, b):
        if b == 0:
            return "Erro: Divisão por zero!"
        return a / b

# chamando métodos estáticos sem criar uma instância da classe
print(Calculadora.somar(5, 3))         # saída : 8
print(Calculadora.subtrair(10, 4))     # saída : 6
print(Calculadora.multiplicar(2, 3))   # saída : 6
print(Calculadora.dividir(8, 2))       # saída : 4.0
print(Calculadora.dividir(8, 0))       # saída : Erro: Divisão por zero!
```

## exercícios métodos estáticos

<details>
<summary>Lista de Exercícios</summary>

1. Crie um método estático em uma classe `Matematica` que calcule e retorne o fatorial de um número.
1. Implemente um método estático `converter_para_maiusculas` em uma classe `Texto` que receba uma string e a retorne em letras maiúsculas.
1. Defina um método estático em uma classe `Utils` que gere um número aleatório entre um intervalo definido.
1. Na classe `Data`, crie um método estático que verifique se um ano é bissexto.
1. Crie um método estático em uma classe `Validador` que valide se um e-mail tem o formato correto.
1. Implemente um método estático `calcular_area_retangulo` em uma classe `Geometria` que receba a largura e a altura e retorne a área.
1. Crie um método estático `formatar_telefone` em uma classe `Contato` que formate um número de telefone para o padrão (XX) XXXXX-XXXX.
1. Na classe `Conversor`, defina um método estático que converta uma temperatura de Celsius para Fahrenheit.
1. Crie um método estático em uma classe `StringUtils` que remova espaços em branco de uma string.
1. Implemente um método estático `gerar_uuid` em uma classe `Identificador` que gere um UUID.
1. Crie um método estático `contar_vogais` em uma classe `AnalisadorDeTexto` que conte o número de vogais em uma string.
1. Na classe `Calculadora`, defina um método estático que calcule a soma de uma lista de números.
1. Crie um método estático em uma classe `ValidadorDeSenha` que verifique se uma senha atende a certos critérios (ex.: tamanho mínimo, presença de números).
1. Implemente um método estático `substituir_espacos` em uma classe `Texto`, que substitua espaços por sublinhados em uma string.
1. Crie um método estático `formatar_data` em uma classe `FormatoData` que formate uma data no padrão DD/MM/AAAA.
1. Na classe `ConversorDeMoeda`, crie um método estático que converta valores entre duas moedas diferentes.
1. Defina um método estático em uma classe `Verificador` que retorne se uma palavra é um palíndromo.
1. Crie um método estático `calcular_media` em uma classe `Estatisticas` que receba uma lista de números e retorne a média.
1. Implemente um método estático `remover_elementos_repetidos` em uma classe `ListaUtils` que retorne uma lista sem elementos duplicados.
1. Na classe `Relogio`, crie um método estático que converta horas de formato 12 horas para 24 horas.

</details>

## métodos de classe

Métodos de classe são uma maneira de definir funções que pertencem à classe em si, e não a uma instância específica da classe. Eles são decorados com o `@classmethod` e recebem a classe como primeiro parâmetro, que é normalmente nomeado como `cls`.

- **definição** : um método de classe é um método que pode ser chamado na própria classe, sem precisar de uma instância. Ele recebe a classe como primeiro argumento, permitindo que você acesse ou modifique atributos da classe;
- **acesso** : ao contrário dos métodos de instância que têm acesso ao estado da instância através de `self`, os métodos de classe têm acesso ao estado da classe através de `cls`;

### quando usar

Métodos de classe são úteis quando:

1. **Manipulação de Atributos de Classe** : se deseja acessar ou modificar atributos que são comuns a todas as instâncias da classe;
1. **Fábricas** : quer implementar métodos que podem criar instâncias da classe de maneiras alternativas (métodos de fábrica);

### como definir

Veja a sintaxe para definir um método estático :

```python
class MinhaClasse:
    @classmethod
    def meu_metodo_de_classe(cls):
        # lógica do método
```

Veja um exemplo prático :

```python
class ContaBancaria:
    taxa_de_juros = 0.05  # atributo da classe

    def __init__(self, saldo):
        self.saldo = saldo

    @classmethod
    def set_taxa_de_juros(cls, nova_taxa):
        cls.taxa_de_juros = nova_taxa

    @classmethod
    def criar_conta(cls, saldo_inicial):
        return cls(saldo_inicial)

    def aplicar_juros(self):
        self.saldo += self.saldo * self.taxa_de_juros

# usando o método de classe para alterar a taxa de juros
print("Taxa de juros atual:", ContaBancaria.taxa_de_juros)  # saída : 0.05
ContaBancaria.set_taxa_de_juros(0.07)
print("Nova taxa de juros:", ContaBancaria.taxa_de_juros)    # saída : 0.07

# usando o método de classe para criar uma nova conta
nova_conta = ContaBancaria.criar_conta(1000)
print("Saldo inicial da nova conta:", nova_conta.saldo)  # saída : 1000

# aplicando juros
nova_conta.aplicar_juros()
print("Saldo após aplicar juros:", nova_conta.saldo)  # saída : 1070.0
```

## exercícios métodos de classe

<details>
<summary>Lista de Exercícios</summary>

1. Crie uma classe `Carro` que tenha um atributo de classe `numero_de_carros` e um método de classe que incremente esse número sempre que um novo carro for criado.
1. Implemente um método de classe `criar_carrinho` em uma classe `CarrinhoDeCompras`, que retorne uma instância de `CarrinhoDeCompras` com uma lista vazia.
1. Defina uma classe `Produto` com um atributo de classe `estoque_total` e um método de classe que retorne o total de produtos em estoque.
1. Crie um método de classe em uma classe `Usuario` que retorne uma lista de todos os usuários cadastrados.
1. Na classe `Conta`, implemente um método de classe `definir_limite` que defina um limite padrão para todas as contas.
1. Crie um método de classe `adicionar_cliente` em uma classe `Banco` que adicione um novo cliente à lista de clientes.
1. Defina um método de classe em uma classe `Funcionario` que conte o número total de funcionários.
1. Crie um método de classe `gerar_id` em uma classe `Registro`, que retorne um ID único cada vez que for chamado.
1. Implemente um método de classe `calcular_media` em uma classe `Notas`, que receba uma lista de notas e retorne a média.
1. Na classe `Livro`, crie um método de classe que retorne uma lista de todos os livros publicados.
1. Crie um método de classe `incrementar_visitas` em uma classe `Pagina`, que incremente o número de visitas a uma página web.
1. Defina um método de classe em uma classe `Equipe` que retorne o número total de membros da equipe.
1. Implemente um método de classe `set_telefone` em uma classe `Contato` que permita atualizar o número de telefone para todos os contatos.
1. Na classe `Transacao`, crie um método de classe que retorne todas as transações de um determinado tipo.
1. Crie um método de classe `criar_arquivo` em uma classe `GeradorDeRelatorios` que crie um novo arquivo de relatório.
1. Defina um método de classe em uma classe `Categoria` que retorne a lista de todas as categorias disponíveis.
1. Implemente um método de classe `adicionar_item` em uma classe `Inventario` que adicione um item ao inventário global.
1. Crie um método de classe `definir_mensagem_padrao` em uma classe `Mensagem` que altere a mensagem padrão para todos os objetos da classe.
1. Na classe `Evento`, crie um método de classe que retorne a lista de todos os eventos agendados.
1. Implemente um método de classe `get_informacoes` em uma classe `Escola` que retorne informações sobre todas as escolas cadastradas.

</details>

## métodos de instância vs estáticos vs de classe

### métodos de instância

1. **Definição**
    - são aqueles que operam em instâncias específicas de uma classe; eles têm acesso ao estado da instância através do parâmetro `self`, que se refere ao objeto atual;

1. **Quando Usar**
    - quando se precisa acessar ou modificar atributos de uma instância específica;
    - quando a lógica do método depende dos dados contidos na instância;

1. **Vantagens**
    - **Acesso ao estado da instância** : podem manipular e acessar dados específicos de cada instância, tornando-os muito flexíveis;
    - **Encapsulamento** : a lógica é organizada em torno da instância, facilitando a leitura e a manutenção do código;

1. **Desvantagens**
    - **Dependência de instância** : necessita de uma instância da classe para ser chamado, o que pode aumentar a sobrecarga de criação de objetos quando não é necessário;
    - **Performance** : acesso a atributos de instância pode ser mais lento em comparação com métodos que não dependem de estado, especialmente em chamadas repetidas;

### métodos de classe

1. **Definição**
    - são métodos que operam na classe como um todo, não em instâncias específicas. Eles são definidos com o decorador `@classmethod` e recebem a classe como primeiro argumento (`cls`);

1. **Quando Usar**
    - quando se precisa manipular ou acessar atributos que pertencem à classe e são compartilhados entre todas as instâncias;
    - para criar métodos de fábrica que instanciam objetos de maneira diferente;

1. **Vantagens**
    - **Acesso ao estado da classe** : podem modificar atributos que são comuns a todas as instâncias, oferecendo um meio de controlar o comportamento da classe como um todo;
    - **Métodos de fábrica** : facilitam a criação de instâncias de maneira mais flexível e centralizada;

1. **Desvantagens**
    - **Menos flexível que métodos de instância** : não têm acesso aos dados específicos de uma instância, o que limita seu uso em alguns contextos;
    - **Possível confusão** : a lógica de negócios pode se tornar confusa se não for bem estruturada, especialmente se muitas operações dependem de atributos de classe;

### métodos estáticos

1. **Definição**
    - são funções definidas dentro do escopo de uma classe que não dependem do estado da instância nem do estado da classe; eles são decorados com `@staticmethod`;

1. **Quando Usar**
    - quando a lógica do método não precisa acessar ou modificar atributos de instância ou de classe;
    - Para agrupar funções que têm uma lógica relacionada à classe, mas que não requerem acesso a `self` ou `cls`;

1. **Vantagens**
    - **Desacoplamento** : não dependem do estado da instância ou da classe, tornando-os mais fáceis de testar e reutilizar;
    - **Organização** : permitem agrupar funções relacionadas à lógica da classe, mantendo o código mais organizado;

1. **Desvantagens**
    - **Sem acesso ao estado** : como não têm acesso a `self` ou `cls`, não podem interagir com atributos de instância ou de classe, limitando seu uso em determinadas situações;
    - **Menos intuitivo** : o uso pode ser menos intuitivo para aqueles que estão acostumados a trabalhar com métodos que interagem com o estado;

### comparação

| Característica         | Métodos de Instância         | Métodos de Classe               | Métodos Estáticos               |
|------------------------|------------------------------|---------------------------------|---------------------------------|
| **Acesso**             | `self` (instância)          | `cls` (classe)                  | Nenhum acesso ao estado         |
| **Quando Usar**        | Manipular dados específicos da instância | Manipular dados da classe ou métodos de fábrica | Lógica que não precisa de estado |
| **Vantagens**          | Flexibilidade e encapsulamento | Controle sobre a classe e seus atributos | Desacoplamento e organização     |
| **Desvantagens**       | Dependência de instância     | Menos flexível em relação a instâncias | Sem acesso ao estado            |

### exemplos

Abaixo há exemplos de criação de classes que abordam os conceitos vistos anteriormente
- [**atributos de instância**](#atributos-de-instância)
- [**atributos de classe**](#atributos-de-classe)
- [**métodos de instância**](#métodos-de-instância)
- [**métodos de classe**](#métodos-de-classe)
- [**métodos estáticos**](#métodos-estáticos)
- [**métodos mágicos**](#métodos-mágicos)

#### Exemplo 1 : Classe `Carro`

**Objetivo**: Um sistema que gerencia veículos, com contador de carros criados e operações entre diferentes carros.

```python
class Carro:
    total_carros = 0

    def __init__(self, marca, modelo, ano, preco):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano
        self.preco = preco
        Carro.total_carros += 1

    def descricao(self):
        return f'{self.marca} {self.modelo} ({self.ano})'

    @classmethod
    def carros_criados(cls):
        return f'Carros criados: {cls.total_carros}'

    @staticmethod
    def depreciacao(preco, anos):
        return preco * (0.9 ** anos)

    def __str__(self):
        return self.descricao()

    def __add__(self, outro_carro):
        return self.preco + outro_carro.preco

    def __lt__(self, outro_carro):
        return self.ano < outro_carro.ano

carro1 = Carro("Toyota", "Corolla", 2020, 90000)
carro2 = Carro("Honda", "Civic", 2019, 85000)

print(carro1)  # Toyota Corolla (2020)
print(carro2)  # Honda Civic (2019)

print(Carro.carros_criados())  # Carros criados: 2
print(Carro.depreciacao(100000, 5))  # 59049.0

print(carro1 + carro2)  # 175000

print(carro1 < carro2)  # False (Corolla é mais novo que Civic)
```

---

#### Exemplo 2 : Classe `Funcionario`

**Objetivo** : Sistema de gerenciamento de funcionários com contagem total e cálculo de salário.

```python
class Funcionario:
    total_funcionarios = 0

    def __init__(self, nome, cargo, salario):
        self.nome = nome
        self.cargo = cargo
        self.salario = salario
        Funcionario.total_funcionarios += 1

    def info(self):
        return f'{self.nome} trabalha como {self.cargo}'

    @classmethod
    def total_funcionarios_cadastrados(cls):
        return f'Total de funcionários: {cls.total_funcionarios}'

    @staticmethod
    def aumento_percentual(salario, percentual):
        return salario * (1 + percentual / 100)

    def __repr__(self):
        return f'Funcionario({self.nome}, {self.cargo}, {self.salario})'

    def __eq__(self, outro_funcionario):
        return self.salario == outro_funcionario.salario

    def __gt__(self, outro_funcionario):
        return self.salario > outro_funcionario.salario

func1 = Funcionario("Alice", "Engenheira", 5000)
func2 = Funcionario("Bob", "Gerente", 6000)

print(func1.info())  # Alice trabalha como Engenheira
print(Funcionario.total_funcionarios_cadastrados())  # Total de funcionários: 2

print(Funcionario.aumento_percentual(5000, 10))  # 5500.0

print(func1 == func2)  # False
print(func1 > func2)  # False
```

---

#### Exemplo 3 : Classe `Livro`

**Objetivo** : Sistema de biblioteca com contagem de livros e operações entre diferentes livros.

```python
class Livro:
    total_livros = 0

    def __init__(self, titulo, autor, paginas):
        self.titulo = titulo
        self.autor = autor
        self.paginas = paginas
        Livro.total_livros += 1

    def detalhes(self):
        return f'{self.titulo} por {self.autor}, {self.paginas} páginas'

    @classmethod
    def total_de_livros(cls):
        return f'Total de livros cadastrados: {cls.total_livros}'

    @staticmethod
    def comparar_paginas(livro1, livro2):
        return livro1.paginas > livro2.paginas

    def __str__(self):
        return self.detalhes()

    def __add__(self, outro_livro):
        return self.paginas + outro_livro.paginas

    def __eq__(self, outro_livro):
        return self.paginas == outro_livro.paginas

livro1 = Livro("1984", "George Orwell", 328)
livro2 = Livro("Brave New World", "Aldous Huxley", 288)

print(livro1)  # 1984 por George Orwell, 328 páginas
print(livro2)  # Brave New World por Aldous Huxley, 288 páginas

print(Livro.total_de_livros())  # Total de livros cadastrados: 2

print(Livro.comparar_paginas(livro1, livro2))  # True

# Soma de páginas
print(livro1 + livro2)  # 616

print(livro1 == livro2)  # False
```

---

#### Exemplo 4 : Classe `Produto`

**Objetivo** : Gerenciamento de produtos com estoque e operações de inventário.

```python
class Produto:
    total_produtos = 0

    def __init__(self, nome, preco, quantidade):
        self.nome = nome
        self.preco = preco
        self.quantidade = quantidade
        Produto.total_produtos += 1

    def info(self):
        return f'{self.nome}: R${self.preco:.2f} (Estoque: {self.quantidade})'

    @classmethod
    def total_estoque(cls):
        return f'Total de produtos cadastrados: {cls.total_produtos}'

    @staticmethod
    def calcular_desconto(preco, desconto):
        return preco - (preco * desconto / 100)

    def __str__(self):
        return self.info()

    def __mul__(self, outro_produto):
        return self.quantidade * self.preco + outro_produto.quantidade * outro_produto.preco

    def __lt__(self, outro_produto):
        return self.preco < outro_produto.preco

produto1 = Produto("Camiseta", 50, 10)
produto2 = Produto("Calça", 80, 5)

print(produto1)  # Camiseta: R$50.00 (Estoque: 10)
print(produto2)  # Calça: R$80.00 (Estoque: 5)

print(Produto.total_estoque())  # Total de produtos cadastrados: 2
print(Produto.calcular_desconto(100, 10))  # 90.0

print(produto1 * produto2)  # 900 (valor total dos produtos em estoque)
print(produto1 < produto2)  # True (Camiseta é mais barata que Calça)
```

---

#### Exemplo 5 : Classe `ContaBancaria`

**Objetivo** : Sistema de contas bancárias com total de contas criadas e operações financeiras.

```python
class ContaBancaria:
    total_contas = 0

    def __init__(self, titular, saldo):
        self.titular = titular
        self.saldo = saldo
        ContaBancaria.total_contas += 1

    def depositar(self, valor):
        self.saldo += valor
        return f'Novo saldo de {self.titular}: R${self.saldo:.2f}'

    @classmethod
    def total_de_contas(cls):
        return f'Total de contas: {cls.total_contas}'

    @staticmethod
    def calcular_juros(saldo, taxa):
        return saldo * (1 + taxa / 100)

    def __str__(self):
        return f'Conta de {self.titular} com saldo de R${self.saldo:.2f}'

    def __sub__(self, outro_conta):
        return self.saldo - outro_conta.saldo

    def __gt__(self, outro_conta):
        return self.saldo > outro_conta.saldo

conta1 = ContaBancaria("Carlos", 1500)
conta2 = ContaBancaria("Ana", 2500)

print(conta1)  # Conta de Carlos com saldo de R$1500.00
print(conta2)  # Conta de Ana com saldo de R$2500.00

print(ContaBancaria.total_de_contas())  # Total de contas: 2
print(ContaBancaria.calcular_juros(1000, 5))  # 1050.0

print(conta2 - conta1)  # 1000
print(conta1 > conta2)  # False
```

---

#### Exemplo 6 : Classe `Pessoa` e Herança com `Funcionario`

**Objetivo** : Criar um sistema que gerencie pessoas e seus derivados, como funcionários, com métodos de fábrica para criação e comparação de idade.

```python
class Pessoa:
    populacao_total = 0

    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade
        Pessoa.populacao_total += 1

    def info(self):
        return f'Nome: {self.nome}, Idade: {self.idade}'

    @classmethod
    def from_string(cls, dados):
        nome, idade = dados.split(',')
        return cls(nome, int(idade))

    @staticmethod
    def maior_idade(idade):
        return idade >= 18

    def __str__(self):
        return f'{self.nome}, {self.idade} anos'

    def __add__(self, outra_pessoa):
        return self.idade + outra_pessoa.idade

    def __eq__(self, outra_pessoa):
        return self.idade == outra_pessoa.idade


class Funcionario(Pessoa):
    def __init__(self, nome, idade, salario):
        super().__init__(nome, idade)
        self.salario = salario

    def info(self):
        return f'{super().info()}, Salário: {self.salario}'

    def __gt__(self, outro_funcionario):
        return self.salario > outro_funcionario.salario


pessoa1 = Pessoa("Carlos", 25)
funcionario1 = Funcionario("Ana", 30, 5000)

print(pessoa1.info())  # Carlos, 25 anos
print(funcionario1.info())  # Nome: Ana, Idade: 30, Salário: 5000

# Fábrica
pessoa2 = Pessoa.from_string("João,40")
print(pessoa2)  # João, 40 anos

print(Pessoa.maior_idade(17))  # False
print(pessoa1 + pessoa2)  # 65 (soma das idades)

funcionario2 = Funcionario("Pedro", 35, 7000)
print(funcionario1 > funcionario2)  # False
```

---

#### Exemplo 7 : Classe `Animal` e Herança com `Cachorro`

**Objetivo** : Gerenciar diferentes tipos de animais com métodos de fábrica para criar animais a partir de dados e operações de idade e raça.

```python
class Animal:
    total_animais = 0

    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade
        Animal.total_animais += 1

    def som(self):
        return "Som genérico"

    @classmethod
    def cria_a_partir_de_string(cls, dados):
        nome, idade = dados.split(',')
        return cls(nome, int(idade))

    @staticmethod
    def expectativa_vida(tipo):
        return 15 if tipo == "Cachorro" else 10

    def __str__(self):
        return f'Animal: {self.nome}, Idade: {self.idade}'

    def __add__(self, outro_animal):
        return self.idade + outro_animal.idade

    def __eq__(self, outro_animal):
        return self.idade == outro_animal.idade


class Cachorro(Animal):
    def __init__(self, nome, idade, raca):
        super().__init__(nome, idade)
        self.raca = raca

    def som(self):
        return "Latido"

    def __gt__(self, outro_cachorro):
        return len(self.raca) > len(outro_cachorro.raca)


animal1 = Animal("Tigre", 4)
cachorro1 = Cachorro("Rex", 3, "Labrador")

print(animal1.info())  # Animal: Tigre, Idade: 4
print(cachorro1.info())  # Animal: Rex, Idade: 3

animal2 = Animal.cria_a_partir_de_string("Leão,5")
print(animal2)  # Animal: Leão, Idade: 5

print(animal1 + animal2)  # 9

cachorro2 = Cachorro("Spike", 4, "Poodle")
print(cachorro1 > cachorro2)  # False

print(Animal.expectativa_vida("Cachorro"))  # 15
```

---

#### Exemplo 8 : Classe `Produto` e Herança com `Eletronico`

**Objetivo**: Sistema de gerenciamento de produtos com métodos de fábrica para criação de produtos e operações de estoque.

```python
class Produto:
    total_produtos = 0

    def __init__(self, nome, preco):
        self.nome = nome
        self.preco = preco
        Produto.total_produtos += 1

    def info(self):
        return f'Produto: {self.nome}, Preço: R${self.preco:.2f}'

    @classmethod
    def cria_a_partir_de_string(cls, dados):
        nome, preco = dados.split(',')
        return cls(nome, float(preco))

    @staticmethod
    def aplicar_desconto(preco, desconto):
        return preco - (preco * desconto / 100)

    def __str__(self):
        return self.info()

    def __add__(self, outro_produto):
        return self.preco + outro_produto.preco

    def __eq__(self, outro_produto):
        return self.preco == outro_produto.preco


class Eletronico(Produto):
    def __init__(self, nome, preco, garantia):
        super().__init__(nome, preco)
        self.garantia = garantia

    def info(self):
        return f'{super().info()}, Garantia: {self.garantia} anos'

    def __gt__(self, outro_eletronico):
        return self.garantia > outro_eletronico.garantia


produto1 = Produto("Mesa", 300)
eletronico1 = Eletronico("Notebook", 2500, 2)

print(produto1.info())  # Produto: Mesa, Preço: R$300.00
print(eletronico1.info())  # Produto: Notebook, Preço: R$2500.00, Garantia: 2 anos

produto2 = Produto.cria_a_partir_de_string("Cadeira,150")
print(produto2)  # Produto: Cadeira, Preço: R$150.00

print(produto1 + produto2)  # 450.0

eletronico2 = Eletronico("TV", 1800, 3)
print(eletronico1 > eletronico2)  # False

print(Produto.aplicar_desconto(1000, 10))  # 900.0
```
