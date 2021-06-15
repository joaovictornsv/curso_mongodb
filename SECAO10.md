<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 10</h1>
  <h2>Seleção de arrays e documents</h2>
</div>

<br/>

## Seleção em embedded documents

Sintaxe diferente: a chave fica entre aspas
```
find({ "chave1.chave2": valor })
```

## Seleção em embedded documents com operador
```
find({ "chave1.chave2": { $gt: 20 } })
```

## Encontrar item específico de array
```diff
# Retorna todos os alunos com nota 8
db.alunos.find({ notas: 8 })

# Retorna somente os alunos com as quatros notas na mesma ordem
db.alunos.find({ notas: [10, 8, 6, 5] })
```

## Alguns valores do array

Operador `$all`
```diff
# Retorna todos os alunos que possuam 8 e 7 em suas notas independente da ordem e tamanho do array
db.alunos.find({ matematica: { $all: [8, 7] } })
```

## Consulta pelo tamanho do array

Operador `$size`
```diff
# Todos os arrays de 4 elementos serão retornados
db.alunos.find({ matematica: { $size: 4 } })
```

## Seleção de array de documents
```diff
# Retorna os registros cuja alguma variação atenda a todos os filtros
db.produtos.find({ variacoes: { cor: 'Verde', tamanho: 'G', qtd: 48 } })
```

## Array de documents e operadores
```diff
db.produtos.find({ "variacoes.qtd": { $gt: 30 } })
```

## Utilizando `$elemMatch`
```diff
# Retorna os registros cuja alguma variação algum dos filtros
db.produtos.find({
  variacoes: { $elemMatch: {
    tamanho: { $gt: 40 },
    cor: 'Azul'
  }}
})
```
Utilizando apenas os filtros comuns (sem o `$elemMath`), a busca procurará por uma variação que atenda a todos os filtros, já com o `$elemMatch`, se a variação atender a apenas um dos filtros, o registro é retornado.

## Retornando campos específicos
```diff
db.pessoas.find({}, { nome: 1, idade: 1 })
```
O _id também será retornado por padrão. O número 1 determina os campos que serão retornados.

## Removendo o _id do retorno
```diff
db.pessoas.find({}, { _id: 0, nome: 1, idade: 1 })
```

## Removendo campos específicos
```diff
db.pessoas.find({}, { altura: 0, cor_dos_olhos: 0})

db.pessoas.find({}, { "caracteristicas.peso": 0 })
```