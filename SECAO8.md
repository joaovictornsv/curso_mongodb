<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 8</h1>
  <h2>Operadores de query</h2>
</div>

<br/>

- Operador de igualdade `$eq`
```
db.restaurants.findOne({ rating: { $eq: 5 } })
```

- Operador de maior e maior ou igual

`$gt`: maior que
`$gte`: maior ou igual que
```
db.restaurants.findOne({ rating: { $gte: 4 }})
```

- Operador de menor e menor ou igual

`$lt`: menor que
`$lte`: menor ou igual que
```
db.restaurants.findOne({ rating: { $lt: 2 }})
```

- Operador `$in`
```
db.restaurants.find({ type_of_food: { $in: ['Pizza', 'Chinese'] } })
```

- Operador `$ne` (not equal)

Inverso de `$eq`
```
db.restaurants.findOne({ rating: { $ne: 5 } })
```

- Operador `$exists`

Retorna apenas dados que possuem determinado campo
```
db.restaurants.find({ high_score: { $exists: true }})
```

- Operador `$text`

Faz uma busca sobre o texto do campo que informado no filtro (semelhante ao LIKE do SQL).

É preciso criar um índice antes de realizar a query.
```diff
# Criando o índice
db.restaurants.createIndex({ name: 'text' })

# Usando o operador
db.restaurants.find({ $text: { $search: 'pizza' } })
```