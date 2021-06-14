# Programação Orientada a Objetos com Python

## 1. Convenções de nomes em Python  

Essas convenções tem um nome que podemos usar para nos referir ao modo como estamos nomeando determinados objetos em nosso programa:

**PascalCase** - significa que todas as palavras iniciam com letra maiúscula e nada é usado para separá-las, como em: `MinhaClasse`, `Classe`, `MeuObjeto`, `MeuProgramaMuitoLegal`.  
Essa á a convenção utilizada para **classes** em Python;

**camelCase** - a única diferença de camelCase para PascalCase é a primeira letra. Em camelCase a primeira letra sempre será minúscula e o restante das palavras deverá iniciar com letra maiúscula. Como em: `minhaFuncao`, `funcaoDeSoma`, etc...  
Essa conversão **não é usada** em Python;

**snake_case** - este é o padrão usado em Python para definir qualquer coisa que não for uma classe.  
Todas as letras serão minúsculas e separadas por um underline, como em: `minha_variavel`, `funcao_legal`, `soma`.

**Portanto os padrões usados em Python são:**  
`snake_case` para qualquer coisa e `PascalCase` para classes.

## 2. Classes
### 2.1 Declarar classe
```python
class Pessoa:
    pass
```

### 2.2 Importar classe
```python
from pessoa import Pessoa
```

## 3. Métodos
### 3.1 Métodos de instância
#### `__init__`
É o construtor da classe, método que é chamado assim que a classe for instanciada.
```python
class Pessoa:
    def __init__(self, nome):
        self.nome = nome
```
#### `self`
Todos **métodos de instância** da classe recebem como primeiro atributo o `self`,  
ele refere-se a instancia que foi criada a partir da classe.

```python
class Pessoa:
    def __init__(self, nome):
        self.nome = nome

    def comer(self, alimento):
        print(f'{self.nome} está comendo {alimento}.')
```

Atributos da classe podem ser declarados no construtor sendo atribuidos os valores que forem passados por parâmetro,
como também serem criados diretos na classe sendo acessiveis para todas instancias criadas através do self.

### 3.2 Métodos da classe
Além dos **métodos de instância** que ficam disponiveis para cada objeto instanciado a partir da classe,  
também podem ser criados métodos próprios da classe onde ficam acessiveis apenas para a classe em si  
e não para objetos instanciados a partir da classe.
Para esse comportamento devemos passar antes um decorator chamado `@classmethod` e o primeiro parâmetro passa a ser a própria classe `(cls)`.
```python
class Pessoa:
    ano_atual = 2021
    
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    @classmethod
    def pessoa_nasc(cls, nome, nasc):
        idade = cls.ano_atual - nasc
        return cls(nome, idade)
```

### 3.3 Métodos estáticos
São métodos que **não recebem** o contexto da instância e da classe,  
poderiam até ser criados fora da classe, mas se necessário podem ser criados dentro da classe.  
Deve-se adicionar um decorator `@staticmethod` antes da assinatura do método.
```python
from random import randint
class Pessoa:    
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    @staticmethod
    def gera_id():
        rand = randint(10000, 19999)
        return rand
```