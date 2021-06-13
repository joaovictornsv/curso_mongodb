<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 5</h1>
  <h2>Atualização de dados</h2>
</div>

<br/>

- Atualizando um dado

O operador `$set` é onde ficam os valores a serem atualizados

```diff
db.<collection>.updateOne({ <filtro> }, { $set: { <atualizações> } })

# Ex
db.books.updateOne({ _id: 314 }, { $set: { pageCount: 1000 } })
```


- Atualizando vários dados
```diff
db.<collection>.updateMany({ <filtro> }, { $set: { <atualizações> } })

# Ex
db.books.updateMany({ categories: "Java" }, { $set: { status: "UNPUBLISHED" } })
```

- Adicionando dados com update
```
db.books.updateMany({ authors: "Vikram Goyal" }, { $set: { downloads: 1000 } })
```

- Trocando todo o documento
```
db.books.replaceOne({ _id: 120 }, { foi: 'substituído' })
```
Trocamos todos os dados do registro com id 120 para o document do segundo parâmetro (preservando apenas o campo `_id`)

- Adicionando item a um array

Operador `$push`
```
db.books.updateOne({ -id: 201 }, { $push: { categories: "PHP" } })
```

- Atualizando todos os itens da collection
```
db.books.updateMany({}, { $set: { atualizado: true } })
``` 