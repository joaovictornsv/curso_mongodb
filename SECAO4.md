<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 4</h1>
  <h2>Leitura de dados</h2>
</div>

<br/>

- Encontrar todos os dados
```diff
db.<collection>.find()

# ou

db.<collection>.find({})
```

- Método `pretty`

É utilizado para trazer uma resposta formatada dos dados.
```
db.<collection>.find().pretty()
```

- Encontrando um dado específico
```diff
db.<collection>.find({ <filtro> })

# Ex:
db.pessoas.find({ name: 'João' })
```

- Encontrando dado entre múltiplos valores

Operador `$in`. Semelhante ao `OR` do SQL
```
db.books.find({ categories: { $in: ['Java', 'Internet'] } })

```

- Múltiplas condições

Semelhante ao `AND` do SQL
```
db.books.find({ pageCount: 532, _id: 63 })

```

- Maior que um valor

Operador `$gt` (greater than)
```
db.books.find({ pageCount: { $gt: 450 } })

```

- Menor que um valor

Operador `$lt` (less than)
```
db.books.find({ pageCount: { $lt: 120 } })

```
- Operador `$or`
```
db.books.find({ $or: [{ pageCount: { $gt: 500 } }, { _id: { $lt: 5 } }] })

```
---
- Quando usar `$or` e `$in`

`$or`: Filtros em campos diferentes

`$in`: Filtros no mesmo campo

---

- `AND` e `OR` na mesma consulta
```
db.books.find({
  status: 'PUBLISH',
  $or: [
    { pageCount: 500 },
    { authors: 'Robin Sen' }
  ]
})

```
---
- Contando número de resultados

Método `count`
```
db.books.find().count()

db.books.find({ pageCount: { $gt: 600 } }).count()
```