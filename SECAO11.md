<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 11</h1>
  <h2>Operadores de update</h2>
</div>

<br/>

## Operador `$inc`

Usado para acrescentar ou diminuir uma quantidade especificada a um valor.
```diff
# Acrescenta 2 ao número de posts
.updateOne({ ... }, { $inc: { postCount: 2 } })
```

## Operador `$min`

Atualiza um valor, caso o especificado do operador seja menor que o do registro.
```diff
.updateOne({ ... }, { $min: { postCount: 0, likesReceived: 0} })
# Zeramos os campos posts e likes
```
## Operador `$max`

Faz o inverso do `$min`, ou seja, atualiza um valor, caso o especificado do operador seja maior que o do registro.
```
.updateOne({ ... }, { $max: { maxPosts: 250 } })
```

## Operador `$mul`

Multiplica o número de alguma propriedade por um outro número definido.
```
.updateOne({ ... }, { $mul: { maxPosts: 2, } })
```

## Operador `$rename`

Renomeia um campo.
```diff
# Renomeamos o campo 'author' para 'author_fullname' em todos os registros
.updateOne({}, { $rename: { author: 'author_fullname' } })
```

## Operador `$unset`

Tem como objetivo remover um campo de um item
```diff
# Remove o campo 'active' de todos os registros
.updateOne({}, { $unset: { active: '' } })
```

## Operador `$addToSet`

Adiciona um ou mais valores em arrays, apenas se eles já não estiverem lá, ou seja, não duplica os elementos.
```diff
.updateOne({ ... }, { $addToSet: { categories: { $each: ['PHP', 'Vue'] } } })
```

## Operador `$pop`

Remove o último ou o primeiro elemento de um array.

- Para remover o primeiro utilize -1
- Para remover o último utilize 1
```diff
Remoção do primeiro elemento do array 'categories'
.updateOne({ ... }, { $pop: { categories: -1 } })
```

## Operador `$push`

Adiciona um ou mais valores a um array
```
.updateOne({ ... }, { $push: { categories: 'Linux' } })
```

## `$push` para mais itens

Para adicionar mais itens com o `$push` precisamos do operador `$each` 
```
.updateOne({ ... }, { $push: { categories: { $each: ['HTML', 'CSS'] } } })
```

## Operador `$pullAll`

Remove vários itens de um array
```
.updateOne({ ... }, { $pullAll: { categories: ['Linux', 'Docker'] } })
```