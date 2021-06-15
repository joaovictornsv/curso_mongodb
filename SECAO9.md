<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 9</h1>
  <h2>Relacionamentos (Modelagem de dados)</h2>
</div>

<br/>

## Embedded documents

A ideia é inserir um document dentro do registro principal. Funciona bem para One to One.<br>
Exemplo:
```javascript
{
  _id: '1111',
  nome: 'João Victor',
  idade: 19,
  endereco: {
    rua: 'Rua 10',
    numero: '123',
    bairro: 'Bairro 1'
  }
}
```

## One to One

Quando um registro possui uma ligação única com outro, e o inverso também é verdadeiro.

Trabalhando com duas collections, precisamos referenciar as duas entidades do relacionamento através do id.

Exemplo:
```javascript
// collection 'pessoas'
{
  _id: '1111',
  nome: 'João Victor',
  idade: 19,
  endereco_id: '2222'
}

// collection 'enderecos'
{
  _id: '2222',
  pessoa_id: '1111',
  rua: 'Rua 10',
  numero: '123',
  bairro: 'Bairro 1'
}
```

## One to Many

Quando um registro pode possuir mais vínculos com uma outra collection, porém o inverso é falso.

Exemplo: usuário que pode fazer várias compras
```javascript
// collection 'pessoas'
{
  _id: '1111',
  nome: 'João Victor',
  idade: 19
}

// collection 'compras'
[
  {
    _id: 'compra1',
    comprador_id: '1111',
    produto: 'Celular',
    preco: 1200
  },
  {
    _id: 'compra2',
    comprador_id: '1111',
    produto: 'Fone de ouvido',
    preco: 90
  },
  {
    _id: 'compra3',
    comprador_id: '1111',
    produto: 'Mouse Bluetooth',
    preco: 120
  }
]
```

## Many to Many

Quando os registros das duas collections possuem mais de uma relação entre si.

Exemplo: Alunos e cursos

Uso de estrutura intermediária, uma collection que irá conter apenas os ids de cursos e alunos.

```javascript
// collection 'pessoas'
{
  _id: '1111',
  nome: 'João Victor',
  idade: 19
},
{
  _id: '2222',
  nome: 'João Victor',
  idade: 19
},
```

```javascript
// collection 'cursos'
[
  {
    _id: 'curso1',
    nome: 'Javascript básico',
  },
  {
    _id: 'curso2',
    nome: 'ReactJS avançado'
  },
  {
    _id: 'curso3',
    nome: 'Node e Express'
  }
]
```

```javascript
// estrutura intermediária: collection 'curso_pessoa'
[
  {
    _id: '...',
    aluno_id: '1111',
    curso_id: 'curso1'
  },
  {
    _id: '...',
    aluno_id: '1111',
    curso_id: 'curso3'
  },
  {
    _id: '...',
    aluno_id: '2222'
    curso_id: 'curso1'
  },
  {
    _id: '...',
    aluno_id: '2222'
    curso_id: 'curso2'
  }
]
```

## Por que criar novas collections?

Trabalhar com embedded documents tem uma certa limitação: cada document pode ter no máximo 16mb.

Subdividir em collections trará mais benefícios a longo prazo.