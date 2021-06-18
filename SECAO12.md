<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 12</h1>
  <h2>Índices no MongoDB</h2>
</div>

<br/>

## Introdução
- **Índices**: Recurso que pode aumentar a eficiência de uma query, ou seja, deixá-la mais rápida.

- O campo `_id` já vem com um índice pré-criado.

- Os dados com índices são checados primeiro em uma seleção.

## Criando Índice
```
db.<collection>.createIndex({ <campo>: 1 })
```

## Índice em embedded documents
```
db.<collection>.createIndex({ 'campo1.campo2': 1 })
```

## Verificando index de collections
```
db.<collection>.getIndexes()
```

## Listar índices de um banco
```javascript
db.getCollectionNames().forEach(function(collection) {

  indexes = db[collection].getIndexes();
  print("Índices de " + collection + ": ");
  printjson(indexes;)

});
```

## Removendo Índices
```
db.<collection>.dropIndex({ <campo>: 1 })
```

## Removendo todos os índices
Todos serão removidos, menos o `_id`.
```
db.<collection>.dropIndexes()
```

## Verificando estratégia de query
O método `explain()` retorna informações sobre como o MongoDB fez a consulta.

## Índices de texto
- Facilita a busca de texto em um campo.
- Podemos ter apenas um índice de texto por collection.
```
db.<collection>.createIndex({ campo: 'text' })
```
## Porque não criar muitos índices?
- Pode diminuir a performance, pois índices desnecessários vão ocupar o lugar dos que precisamos.